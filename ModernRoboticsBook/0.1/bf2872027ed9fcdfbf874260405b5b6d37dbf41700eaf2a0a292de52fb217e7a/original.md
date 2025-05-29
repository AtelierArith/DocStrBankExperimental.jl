```
IKinBody(Blist, M, T, thetalist0, eomg, ev)
```

Computes inverse kinematics in the body frame for an open chain robot.

# Examples

```jldoctest; setup = :(using ModernRoboticsBook)
julia> Blist = [  0  0 -1  2  0  0   ;
                  0  0  0  0  1  0   ;
                  0  0  1  0  0  0.1 ]';

julia> M = [ -1  0  0  0 ;
              0  1  0  6 ;
              0  0 -1  2 ;
              0  0  0  1 ];

julia> T = [ 0  1  0     -5 ;
             1  0  0      4 ;
             0  0 -1 1.6858 ;
             0  0  0      1 ];

julia> thetalist0 = [1.5, 2.5, 3];

julia> eomg, ev = 0.01, 0.001;

julia> IKinBody(Blist, M, T, thetalist0, eomg, ev)
([1.5707381937148923, 2.999666997382942, 3.141539129217613], true)
```
