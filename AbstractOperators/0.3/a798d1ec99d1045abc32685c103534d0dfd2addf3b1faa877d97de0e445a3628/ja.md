`displacement(A::AbstractOperator)`

オペレーターの変位を返します。

```julia
julia> A = AffineAdd(Eye(4),[1.;2.;3.;4.])
I+d  ℝ^4 -> ℝ^4

julia> displacement(A)
4-element Array{Float64,1}:
 1.0
 2.0
 3.0
 4.0

```
