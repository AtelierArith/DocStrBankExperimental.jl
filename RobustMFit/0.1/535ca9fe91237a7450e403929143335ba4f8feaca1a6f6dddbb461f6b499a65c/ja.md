```
MTP(μ::Vector{Real}, d::UnivariateDistribution)
```

一変量分布のパラメータにモーメントをマッピングします。`μ`は、推定されるパラメータの数pに対して、分布の最初のp個の生モーメントのベクトルでなければなりません。分布`d`のパラメータは無視されます。

25の一般的に使用される分布に対して、ハードコーディングされた閉じた形式です。いくつかの分布（8つ）は、解析的に解決できない場合、数値的なルート探索に依存します。最悪の場合：数値的なルート探索とモーメントの数値計算。

# 例

```julia
d1 = Normal()
MTP([1, 5], d1)
d2 = Poisson(10)
MTP([5], d2)
```

効果的なパラメータの数については[`nParEff`](@ref nParEff)を、パラメータからモーメントへの逆マッピングについては[`PTM`](@ref PTM)を参照してください。
