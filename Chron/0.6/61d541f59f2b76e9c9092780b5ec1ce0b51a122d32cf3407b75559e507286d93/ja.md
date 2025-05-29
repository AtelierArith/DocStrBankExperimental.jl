```julia
tMinDistMetropolis(smpl::ChronAgeData, nsteps::Int, burnin::Int, dist::Array{Float64})
```

`smpl` 構造体で定義された各サンプルの最小限の制限（噴出/堆積）年齢を計算します。これは、各サンプルの鉱物年齢がソース分布 `dist` から引き出されると仮定して、`Isoplot.metropolis_min` 関数を使用します。結果として得られた定常分布に `BilinearExponential` 関数をフィットさせ、結果を `smpl.Params` に格納して `StratMetropolisDist` 関数で使用します。

`smpl.Path` に提供されたサンプルが U-Pb 同位体データファイルの5列形式のcsvファイルである場合、これらは次の列として解釈されます。

```
| ²⁰⁷Pb/²³⁵U | uncert (absolute) | ²⁰⁶Pb/²³⁸U | uncert (absolute) | correlation |
```

この場合、Pb損失を考慮した噴出/堆積年齢の推定が行われます。それ以外の場合、各データファイルの最初の2列は次のように解釈されます。

```
| Age | Age uncert (absolute) |
```

この場合、標準的な噴出/堆積年齢の推定が行われます。

すべての場合において、不確実性は `smpl.inputSigmaLevel` の値に基づいて1シグマまたは2シグマの*絶対*として扱われます。

### 例

```julia
smpl = tMinDistMetropolis(smpl, 10^6, 10^5, HalfNormalDistribution)
```
