```
EndEffectorForces(thetalist, Ftip, Mlist, Glist, Slist)
```

Computes the joint forces/torques an open chain robot requires only to create the end-effector force `Ftip`.

# Arguments

  * `thetalist`: the $n$-vector of joint variables.
  * `Ftip`: the spatial force applied by the end-effector expressed in frame `{n+1}`.
  * `Mlist`: the list of link frames `i` relative to `i-1` at the home position.
  * `Glist`: the spatial inertia matrices `Gi` of the links.
  * `Slist`: the screw axes `Si` of the joints in a space frame, in the format of a matrix with axes as the columns.

Returns the joint forces and torques required only to create the end-effector force `Ftip`. This function calls InverseDynamics with `g = 0`, `dthetalist = 0`, and `ddthetalist = 0`.

# Examples

```jldoctest; setup = :(using ModernRoboticsBook)
julia> import LinearAlgebra as LA

julia> thetalist = [0.1, 0.1, 0.1]
3-element Vector{Float64}:
 0.1
 0.1
 0.1

julia> Ftip = [1, 1, 1, 1, 1, 1]
6-element Vector{Int64}:
 1
 1
 1
 1
 1
 1

julia> M01 = [1 0 0        0;
              0 1 0        0;
              0 0 1 0.089159;
              0 0 0        1]
4×4 Matrix{Float64}:
 1.0  0.0  0.0  0.0
 0.0  1.0  0.0  0.0
 0.0  0.0  1.0  0.089159
 0.0  0.0  0.0  1.0

julia> M12 = [ 0 0 1    0.28;
               0 1 0 0.13585;
              -1 0 0       0;
               0 0 0       1]
4×4 Matrix{Float64}:
  0.0  0.0  1.0  0.28
  0.0  1.0  0.0  0.13585
 -1.0  0.0  0.0  0.0
  0.0  0.0  0.0  1.0

julia> M23 = [1 0 0       0;
              0 1 0 -0.1197;
              0 0 1   0.395;
              0 0 0       1]
4×4 Matrix{Float64}:
 1.0  0.0  0.0   0.0
 0.0  1.0  0.0  -0.1197
 0.0  0.0  1.0   0.395
 0.0  0.0  0.0   1.0

julia> M34 = [1 0 0       0;
              0 1 0       0;
              0 0 1 0.14225;
              0 0 0       1]
4×4 Matrix{Float64}:
 1.0  0.0  0.0  0.0
 0.0  1.0  0.0  0.0
 0.0  0.0  1.0  0.14225
 0.0  0.0  0.0  1.0

julia> Mlist = [M01, M12, M23, M34]
4-element Vector{Matrix{Float64}}:
 [1.0 0.0 0.0 0.0; 0.0 1.0 0.0 0.0; 0.0 0.0 1.0 0.089159; 0.0 0.0 0.0 1.0]
 [0.0 0.0 1.0 0.28; 0.0 1.0 0.0 0.13585; -1.0 0.0 0.0 0.0; 0.0 0.0 0.0 1.0]
 [1.0 0.0 0.0 0.0; 0.0 1.0 0.0 -0.1197; 0.0 0.0 1.0 0.395; 0.0 0.0 0.0 1.0]
 [1.0 0.0 0.0 0.0; 0.0 1.0 0.0 0.0; 0.0 0.0 1.0 0.14225; 0.0 0.0 0.0 1.0]

julia> G1 = LA.Diagonal([0.010267, 0.010267, 0.00666, 3.7, 3.7, 3.7])
6×6 LinearAlgebra.Diagonal{Float64, Vector{Float64}}:
 0.010267   ⋅         ⋅        ⋅    ⋅    ⋅ 
  ⋅        0.010267   ⋅        ⋅    ⋅    ⋅ 
  ⋅         ⋅        0.00666   ⋅    ⋅    ⋅ 
  ⋅         ⋅         ⋅       3.7   ⋅    ⋅ 
  ⋅         ⋅         ⋅        ⋅   3.7   ⋅ 
  ⋅         ⋅         ⋅        ⋅    ⋅   3.7

julia> G2 = LA.Diagonal([0.22689, 0.22689, 0.0151074, 8.393, 8.393, 8.393])
6×6 LinearAlgebra.Diagonal{Float64, Vector{Float64}}:
 0.22689   ⋅        ⋅          ⋅      ⋅      ⋅ 
  ⋅       0.22689   ⋅          ⋅      ⋅      ⋅ 
  ⋅        ⋅       0.0151074   ⋅      ⋅      ⋅ 
  ⋅        ⋅        ⋅         8.393   ⋅      ⋅ 
  ⋅        ⋅        ⋅          ⋅     8.393   ⋅ 
  ⋅        ⋅        ⋅          ⋅      ⋅     8.393

julia> G3 = LA.Diagonal([0.0494433, 0.0494433, 0.004095, 2.275, 2.275, 2.275])
6×6 LinearAlgebra.Diagonal{Float64, Vector{Float64}}:
 0.0494433   ⋅          ⋅         ⋅      ⋅      ⋅ 
  ⋅         0.0494433   ⋅         ⋅      ⋅      ⋅ 
  ⋅          ⋅         0.004095   ⋅      ⋅      ⋅ 
  ⋅          ⋅          ⋅        2.275   ⋅      ⋅ 
  ⋅          ⋅          ⋅         ⋅     2.275   ⋅ 
  ⋅          ⋅          ⋅         ⋅      ⋅     2.275

julia> Glist = [G1, G2, G3]
3-element Vector{LinearAlgebra.Diagonal{Float64, Vector{Float64}}}:
 [0.010267 0.0 … 0.0 0.0; 0.0 0.010267 … 0.0 0.0; … ; 0.0 0.0 … 3.7 0.0; 0.0 0.0 … 0.0 3.7]
 [0.22689 0.0 … 0.0 0.0; 0.0 0.22689 … 0.0 0.0; … ; 0.0 0.0 … 8.393 0.0; 0.0 0.0 … 0.0 8.393]
 [0.0494433 0.0 … 0.0 0.0; 0.0 0.0494433 … 0.0 0.0; … ; 0.0 0.0 … 2.275 0.0; 0.0 0.0 … 0.0 2.275]

julia> Slist = [ 1  0  1      0  1      0;
                 0  1  0 -0.089  0      0;
                 0  1  0 -0.089  0  0.425]'
6×3 adjoint(::Matrix{Float64}) with eltype Float64:
 1.0   0.0     0.0
 0.0   1.0     1.0
 1.0   0.0     0.0
 0.0  -0.089  -0.089
 1.0   0.0     0.0
 0.0   0.0     0.425

julia> EndEffectorForces(thetalist, Ftip, Mlist, Glist, Slist)
3-element Vector{Float64}:
 1.4095460782639782
 1.857714972318063
 1.392409
```
