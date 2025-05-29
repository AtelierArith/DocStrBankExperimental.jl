```
RenyiDivergence(α::Real)
renyi_divergence(P, Q, α::Real)
```

αの順序のレーニー前距離を作成します。

レーニーは、クルバック–ライブラー発散を一般化する発散測度のスペクトルを定義しました（`KLDivergence`を参照）。この発散は対称ではないため、半距離ではありません。これはパラメータαによってパラメータ化され、α = 1のときにクルバック–ライブラー発散に等しくなります：

α = 0のとき、$R_0(P | Q) = -log(sum_{i: p_i > 0}(q_i))$

α = 1のとき、$R_1(P | Q) = sum_{i: p_i > 0}(p_i log(p_i / q_i))$

α = ∞のとき、$R_∞(P | Q) = log(sup_{i: p_i > 0}(p_i / q_i))$

それ以外の場合、$R_α(P | Q) = log(sum_{i: p_i > 0}((p_i ^ α) / (q_i ^ (α - 1))) / (α - 1)$

# 例：

```jldoctest
julia> x = reshape([0.1, 0.3, 0.4, 0.2], 2, 2);

julia> pairwise(RenyiDivergence(0), x, x)
2×2 Array{Float64,2}:
 0.0  0.0
 0.0  0.0

julia> pairwise(Euclidean(2), x, x)
2×2 Array{Float64,2}:
 0.0       0.577315
 0.655407  0.0
```
