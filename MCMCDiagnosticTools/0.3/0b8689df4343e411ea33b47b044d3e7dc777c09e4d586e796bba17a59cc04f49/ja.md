```
mcse(samples::AbstractArray{<:Union{Missing,Real}}; kind=Statistics.mean, kwargs...)
```

推定量 `kind` が `samples` に適用されるモンテカルロ標準誤差 (MCSE) を推定します。`samples` の形状は `(draws, [chains[, parameters...]])` です。

参照: [`ess`](@ref)

## MCSE推定の種類

MCSEを推定すべき推定量は `kind` で指定されます。`kind` は `samples` と同じ `eltype` のベクトルを受け入れ、実数の推定値を返す必要があります。

以下の推定量については、実効サンプルサイズ [`ess`](@ref) と漸近分散の推定値を使用してMCSEを計算し、`kwargs` は `ess` に転送されます：

  * [`Statistics.mean`](@extref)
  * [`Statistics.median`](@extref)
  * [`Statistics.std`](@extref)
  * `Base.Fix2(Statistics.quantile, p::Real)`

他の推定量については、サブサンプリングブートストラップ法 (SBM)[^FlegalJones2011][^Flegal2012] がフォールバックとして使用され、受け入れられる `kwargs` は `batch_size` のみで、これはMCSEを推定するために使用される重複バッチのサイズを示し、デフォルトは `floor(Int, sqrt(draws * chains))` です。SBMは特に高い自己相関を持つチェーンに対してMCSEを過小評価する傾向があることに注意してください。自己相関が低いことを確認するために、バルク-およびテール-ESS値をチェックする必要があります。

[^FlegalJones2011]: Flegal JM, Jones GL. (2011) MCMCの実装: 自信を持って推定する。                 マルコフ連鎖モンテカルロハンドブック。 pp. 175-97.                 [pdf](http://faculty.ucr.edu/~jflegal/EstimatingWithConfidence.pdf)

[^Flegal2012]: Flegal JM. (2012) マルコフ連鎖モンテカルロにおけるサブサンプリングブートストラップ法の適用性。            モンテカルロおよび準モンテカルロ法 2010。 pp. 363-72.            doi: [10.1007/978-3-642-27440-4_18](https://doi.org/10.1007/978-3-642-27440-4_18)

```
