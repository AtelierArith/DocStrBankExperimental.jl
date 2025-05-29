```
get_overlap(prob1::MeasurementProbability, prob2::MeasurementProbability) -> Float64
```

重み付きオーバーラップ `\2^N sum_s (-2)^{-D[s,s']}P(s)P(s')]` を計算するために、各キュービットインデックスに対してハミングテンソルを順次適用し、2番目の確率テンソルと収束させます。

# 引数

  * `prob1::MeasurementProbability`: 量子状態 `rho1` を表す最初のボルン確率テンソル。
  * `prob2::MeasurementProbability`: 量子状態 `rho2` を表す2番目のボルン確率テンソル。

# 戻り値

  * `weighted_overlap::Float64`: 適切にスケーリングされた計算されたトレース `Tr(rho1 rho2)`。

# 例

```julia
using ITensors

# prob1 と prob2 は事前に定義された MeasurementProbabilities とします
overlap = get_overlap(prob1, prob2)
println("Overlap: ", overlap)
```
