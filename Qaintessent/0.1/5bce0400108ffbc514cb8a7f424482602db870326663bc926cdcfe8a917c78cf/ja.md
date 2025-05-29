```
matrix(::AbstractGate)
```

は[`AbstractGate`](@ref)オブジェクトの密行列表現を返します

# 例

```jldoctest
julia> matrix(X)
2×2 Array{Complex{Float64},2}:
 0.0+0.0im  1.0+0.0im
 1.0+0.0im  0.0+0.0im
```
