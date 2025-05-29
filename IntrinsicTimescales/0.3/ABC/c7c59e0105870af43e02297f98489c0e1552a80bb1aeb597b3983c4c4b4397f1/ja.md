```
ABCResults
```

ABC結果のコンテナで、プロットインターフェースを標準化します。

# フィールド

  * `theta_history::Vector{Matrix{Float64}}`: イテレーションを通じたパラメータ値の履歴
  * `epsilon_history::Vector{Float64}`: イプシロン値の履歴
  * `acc_rate_history::Vector{Float64}`: 受け入れ率の履歴
  * `weights_history::Vector{Vector{Float64}}`: 重みの履歴
  * `final_theta::Matrix{Float64}`: 最終的に受け入れられたパラメータ値
  * `final_weights::Vector{Float64}`: 最終的な重み
