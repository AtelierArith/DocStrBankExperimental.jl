```
anneal(problem::Problem, beta::Vector{Float64}, gamma::Vector{Float64})
```

与えられた問題に対して量子アニーリングを行うための追加関数です。QAOAの代わりに使用します。

### 入力

  * `problem::Problem`: 最適化問題を定義する`Problem`インスタンス。
  * `beta::Vector{Float64}`: 横場またはドライバーハミルトニアンを掛けるスケジュールパラメータのベクトル。
  * `gamma::Vector{Float64}`: 問題または計算基底ハミルトニアンを掛けるスケジュールパラメータのベクトル。

### 出力

  * `probabilities::Vector{Float64}`: ビット列に対する出力確率のベクトル。

### 注意事項

パラメータ`beta`と`gamma`の良い選択は、https://arxiv.org/abs/1907.02359の付録Aに示されています。``
