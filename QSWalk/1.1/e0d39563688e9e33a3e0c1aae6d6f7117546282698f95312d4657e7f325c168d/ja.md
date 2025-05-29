```
unres(vector)
```

`vector`の要素からなる正方行列を返します。`vector`は完全平方数の引数を持つことが期待されます。

# 例

```jldoctest; setup = :(using QSWalk)
julia> v = collect(1:9)*im
9-element Array{Complex{Int64},1}:
 0 + 1im
 0 + 2im
 0 + 3im
 0 + 4im
 0 + 5im
 0 + 6im
 0 + 7im
 0 + 8im
 0 + 9im

julia> unres(v)
3×3 LinearAlgebra.Transpose{Complex{Int64},Array{Complex{Int64},2}}:
 0+1im  0+2im  0+3im
 0+4im  0+5im  0+6im
 0+7im  0+8im  0+9im

julia> res(unres(v)) == v
true
```
