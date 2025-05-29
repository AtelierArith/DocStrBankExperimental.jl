```
JacobiWeight{T}(a,b)
JacobiWeight(a,b)
```

区間 $[-1,1]$ におけるジャコビ重み関数 $(1-x)^a (1+x)^b$ を表す準ベクトル。[`jacobiweight`](@ref) および [`Jacobi`](@ref) も参照してください。

# 例

```jldoctest
julia> J=JacobiWeight(1.0,1.0)
(1-x)^1.0 * (1+x)^1.0 on -1..1

julia> J[0.5]
0.75

julia> axes(J)
(Inclusion(-1.0 .. 1.0 (Chebyshev)),)
```
