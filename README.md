openGL_Smooth_Line
==================

How to draw smooth line (OpenGL on iOS) 

NOTE - Code is not presented since that's still running in the commercial product, but anyway it should be quite easy to implement based on the idea below.

    JERRY ALGORITHM OF FAST DRAWING ARC
 
    for three points a c-(stands for control point) b, by step number, step must be odd
 
    for both x,y:
    d1 = c - a;
    d2 = b - c;
 
    for all d:
    dStep = d/step;
 
    for all dStep: - this is the key of the algorthim - the change rate of the change
    ddStep = dStep/step;
 
    if we need draw a to b arc controlled by c with each step, we can know each step's position
 
    stepi = step(i-1) + d1Step + d2Step + dd1Step(step/2 - i) + dd2Step(i - step/2)
            
    basic ideas is 
 
    1. Overall, each step needs to make the position change of dstep
    2. But when it nears A, the dStep a -> c needs to influence more on the delta, while oppsitely the influence of c -> b needs to be weaken during that time.  Vice versa for c -> b.
    3. The sum of the all steps' influence delta needes to be 0. After all, the dstep * step is all we need.
 
    PS - tradition algorithm that you may find online:
    1. find the center of circel that goes through these three points. 
    2. mark out the radius to them.
    3. move the radius by angle through three points. 
