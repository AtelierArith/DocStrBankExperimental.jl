```
RegressionBasedDID <: DiffinDiffsEstimator
```

回帰ベースの差分の差分の推定手順。

この手順のための `StatsSpec` は以下の引数を受け入れます：

| キー                 | 型の制限                                        | デフォルト値                     | 説明                                                   |
|:------------------ |:------------------------------------------- |:-------------------------- |:---------------------------------------------------- |
| `data`             |                                             |                            | `Tables.jl` 互換のデータテーブル                               |
| `tr`               | `DynamicTreatment{SharpDesign}`             |                            | 処理仕様                                                 |
| `pr`               | `TrendOrUnspecifiedPR{Unconditional,Exact}` |                            | 平行トレンドの仮定                                            |
| `yterm`            | `AbstractTerm`                              |                            | 結果変数のための項                                            |
| `treatname`        | `Symbol`                                    |                            | 処理時間を表す変数の列名                                         |
| `subset`           | `Union{BitVector,Nothing}`                  | `nothing`                  | 推定に使用する `data` の行                                    |
| `weightname`       | `Union{Symbol,Nothing}`                     | `nothing`                  | サンプル重み変数の列名                                          |
| `vce`              | `Vcov.CovarianceEstimator`                  | `Vcov.CovarianceEstimator` | 分散共分散推定量                                             |
| `treatintterms`    | `TermSet`                                   | `TermSet()`                | 処理指標と相互作用する項                                         |
| `xterms`           | `TermSet`                                   | `TermSet()`                | 共変量および固定効果のための項                                      |
| `contrasts`        | `Union{Dict{Symbol,Any},Nothing}`           | `nothing`                  | `StatsModels.jl` によって処理されるコントラストコーディング               |
| `drop_singletons`  | `Bool`                                      | `true`                     | 固定効果のために単一観測を削除する                                    |
| `nfethreads`       | `Int`                                       | `Threads.nthreads()`       | 固定効果を解決するために使用されるスレッドの数                              |
| `fetol`            | `Float64`                                   | `1e-8`                     | 固定効果ソルバーのための許容レベル                                    |
| `femaxiter`        | `Int`                                       | `10000`                    | 固定効果ソルバーに許可される最大反復回数                                 |
| `cohortinteracted` | `Bool`                                      | `true`                     | 処理指標を処理時間で相互作用させる                                    |
| `solvelsweights`   | `Bool`                                      | `false`                    | デフォルトのセルパーティションでセルレベルの最小二乗重みを解決する                    |
| `lswtnames`        | `Iterable of Symbol`s                       | `tuple()`                  | 最小二乗重みを解決するために使用されるセルパーティションを定義する `treatcells` からの列名 |
