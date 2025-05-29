```
 mvnormcdf(Σ::AbstractMatrix, a::AbstractVector, b::AbstractVector; m::Integer = 1000*size(Σ,1), rng = RandomDevice())
```

非中心MVN分布（平均がゼロでないもの）は、積分限界を調整することでこの関数を使用できます。各積分ベクトルから平均ベクトルμを引いてください。

# 例

```julia
Σ = [4 2; 2 3]
μ = [1; 2]
a = [-Inf; -Inf]
b = [2; 2]
(p,e) = mvnormcdf(Σ, a-μ, b-μ)
#(0.4306346895870772, 0.00015776288569406053)
```
