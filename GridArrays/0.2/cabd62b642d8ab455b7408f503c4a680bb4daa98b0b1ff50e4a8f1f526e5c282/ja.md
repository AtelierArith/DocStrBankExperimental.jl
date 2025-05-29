```
struct ChebyshevNodes{T} <: AbstractIntervalGrid{T}
```

[-1,1]のチェビシェフノードを持つグリッド。

# 例

```jldocs
julia> ChebyshevExtremae(4)
4-element ChebyshevExtremae{Float64}:
  1.0
  0.5000000000000001
 -0.4999999999999998
 -1.0
```
