```
MultiFractalField(cov, torus, scov, γ)
```

間欠性パラメータ `γ` を持つ多重フラクタル乱数場。

`scov<:SingularCovariance` は、ガウス乗法的混沌を生成するために必要です。

# 例

```jldoctest
julia> torus = Torus(100, 0.1)
Torus{Float64, Float64}(n=100,η=0.1)

julia> lincov = Linear(0.5)
Linear{Float64}(ξ=0.5, λ=1.0, σ²=1.0)

julia> MultiFractalField(lincov, torus, Log(), 0.4)
MultiFractalField(γ=0.4,cov=Linear{Float64}(ξ=0.5, λ=1.0, σ²=1.0),torus=Torus{Float64, Float64}(n=100,η=0.1))
```
