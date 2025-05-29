`Pol(x::AbstractVector,y::AbstractVector)`

補間: 点 `x` で値 `y` を取る最小次数の非負評価の `Pol` を見つけます。関数が型安定であるためには、値 `y` は体に属している必要があります。

```julia-repl
julia> p=Pol([1,1,1])
Pol{Int64}: q²+q+1

julia> vals=p.(1:5)
5-element Vector{Int64}:
  3
  7
 13
 21
 31

julia> Pol(1:5,vals*1//1)
Pol{Rational{Int64}}: q²+q+1

julia> Pol(1:5,vals*1.0)
Pol{Float64}: 1.0q²+1.0q+1.0
```
