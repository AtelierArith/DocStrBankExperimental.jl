`AffineAdd(A::AbstractOperator, d, [sign = true])`

Affine addition to `AbstractOperator` with an array or scalar `d`. 

Use `sign = false` to perform subtraction.

```julia
julia> A = AffineAdd(Sin(3),[1.;2.;3.])
sin+d  ℝ^3 -> ℝ^3

julia> A*[3.;4.;5.] == sin.([3.;4.;5.]).+[1.;2.;3.]
true

julia> A = AffineAdd(Exp(3),[1.;2.;3.],false)
e-d  ℝ^3 -> ℝ^3

julia> A*[3.;4.;5.] == exp.([3.;4.;5.]).-[1.;2.;3.]
true

```
