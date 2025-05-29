```
JacobianBody(Blist, thetalist)
```

Computes the body Jacobian for an open chain robot.

# Examples

```jldoctest; setup = :(using ModernRoboticsBook)
julia> Blist = [0 0 1   0 0.2 0.2;
                1 0 0   2   0   3;
                0 1 0   0   2   1;
                1 0 0 0.2 0.3 0.4]';

julia> thetalist = [0.2, 1.1, 0.1, 1.2];

julia> JacobianBody(Blist, thetalist)
6×4 Matrix{Float64}:
 -0.0452841  0.995004    0.0       1.0
  0.743593   0.0930486   0.362358  0.0
 -0.667097   0.0361754  -0.932039  0.0
  2.32586    1.66809     0.564108  0.2
 -1.44321    2.94561     1.43307   0.3
 -2.0664     1.82882    -1.58869   0.4
```
