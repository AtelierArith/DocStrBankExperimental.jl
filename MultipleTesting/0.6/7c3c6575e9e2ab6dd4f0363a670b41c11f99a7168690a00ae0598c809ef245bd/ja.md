ベータ一様混合（BUM）モデル

# 引数

  * π0 : 完全モデルに対する一様分布の寄与割合
  * α, β : ベータ分布のパラメータ、Float64、デフォルト: 0.5, 3.0

# 戻り値

`MixtureModel`、`Distributions`パッケージで定義されており、以下で構成されます。

  * 重み/事前確率 π₀ の区間 [0, 1] の一様分布
  * パラメータ α と β を持つベータ分布、重み/事前確率 1-π₀

# 例

```jldoctest
julia> bum = BetaUniformMixtureModel(0.2, 0.5, 1.0);

julia> using Distributions

julia> pdf.(bum, 0.2:0.2:1.0)
5-element Array{Float64,1}:
 1.094427190999916
 0.832455532033676
 0.7163977794943224
 0.647213595499958
 0.6000000000000001

```

# 参考文献

Pounds, S., and Morris, S.W. (2003). Estimating the occurrence of false positives and false negatives in microarray studies by approximating and partitioning the empirical distribution of p-values. Bioinformatics 19, 1236–1242.
