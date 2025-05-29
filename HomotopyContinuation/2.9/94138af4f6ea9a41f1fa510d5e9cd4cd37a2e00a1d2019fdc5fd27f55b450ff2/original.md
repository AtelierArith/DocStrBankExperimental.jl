```
LinearSubspace(A, b)
```

An $m$-dimensional (affine) linear subspace $L$ in $n$-dimensional space given by the extrinsic description $L = \{ x | A x = b \}$.

```julia-repl
julia> A = LinearSubspace([1 0 3; 2 1 3], [5, -2])
1-dim. (affine) linear subspace {x|Ax=b} with eltype Float64:
A:
2×3 Array{Float64,2}:
 1.0  0.0  3.0
 2.0  1.0  3.0
b:
2-element Array{Float64,1}:
  5.0
 -2.0

julia> dim(A)
1

julia> codim(A)
2

julia> ambient_dim(A)
3
```

A `LinearSubspace` holds always its [`extrinsic`](@ref) description, see also [`ExtrinsicDescription`](@ref), as well as its [`intrinsic`](@ref) description, see [`IntrinsicDescription`](@ref).

```julia-repl
julia> intrinsic(A)
IntrinsicDescription{Float64}:
A:
3×1 Array{Float64,2}:
 -0.6882472016116853
  0.6882472016116853
  0.22941573387056186
b₀:
3-element Array{Float64,1}:
 -3.0526315789473677
 -3.947368421052632
  2.684210526315789
```

A `LinearSubspace` can be evaluated with either using [`Intrinsic`](@ref) or [`Extrinsic`](@ref) coordinates.

```julia-repl
julia> u = [0.5]
1-element Array{Float64,1}:
 0.5

julia> x = A(u, Intrinsic)
3-element Array{Float64,1}:
 -3.3967551797532103
 -3.6032448202467893
  2.79891839325107

julia> A(x, Extrinsic)
  2-element Array{Float64,1}:
   0.0
   0.0
```

To change the used coordinates you can use [`coord_change`](@ref).

```julia-repl
julia> coord_change(A, Extrinsic, Intrinsic, x)
1-element Array{Float64,1}:
 0.49999999999999994
```
