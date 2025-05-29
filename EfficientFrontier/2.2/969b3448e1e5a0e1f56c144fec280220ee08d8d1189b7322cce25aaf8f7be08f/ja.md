```
    Problem(E::Vector{T}, V; u, d, G, g, A, b, equilibrate) where T
    Problem(E::Vector{T}, V, u; equilibrate) where T
    Problem(E::Vector{T}, V, u, d; equilibrate) where T
    Problem(E::Vector{T}, V, u, d, G, g; equilibrate) where T
    Problem(E::Vector{T}, V, u, d, G, g, A, b; equilibrate) where T
```

ポートフォリオ選択モデルを設定します：平均ベクトル E と分散行列 V に対して

$$
	min     (1/2)z′Vz - L⋅z′E
	s.t.    Az  = b     ∈ R^{M}
	        Gz  ≤ g     ∈ R^{J}
	        d ≤ z ≤ u   ∈ R^{N}
$$

L=+∞ から L=0 まで。デフォルト値：u = +∞、d = 0、G = []、g = []、A = ones(1,N)、b = [1]、および equilibrate = false

# 例

```
    using EfficientFrontier
    V = [1/100 1/80 1/100
        1/80 1/16 1/40
        1/100 1/40 1/25]    #分散行列
    E = [109 / 100; 23 / 20; 119 / 100] #平均ベクトル
    P = Problem(E, V)   #デフォルトモデル、ショートセールなし
    aCL = EfficientFrontier.ECL(P)  #すべてのクリティカルラインを計算
    aEF = eFrontier(aCL, P)     #効率的フロンティアを計算
    mu = (aEF.mu[1]+aEF.mu[end])/2  #効率的フロンティアの中間のmu
    z = ePortfolio(mu, aEF)     #muに与えられた効率的ポートフォリオの重み

```

[`Documentation for EfficientFrontier.jl`](https://github.com/PharosAbad/EfficientFrontier.jl/wiki) を参照してください

また、[`EfficientFrontier.ECL`](@ref)、[`eFrontier`](@ref)、[`ePortfolio`](@ref) も参照してください
