`AffineAdd(A::AbstractOperator, d, [sign = true])`

`AbstractOperator`に配列またはスカラー`d`を使ったアフィン加算。

`sign = false`を使用すると、減算を行います。

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
