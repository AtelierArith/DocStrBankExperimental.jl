```
anneal(problem::Problem, schedule::Function, T::Float64)
```

与えられた問題に対して量子アニーリングを行うための追加関数です。QAOAの代わりに使用します。

### 入力

  * `problem::Problem`: 最適化問題を定義する`Problem`インスタンス。
  * `schedule::Function`: アニーリングスケジュールを指定する関数（下記参照）。
  * `T::Float64`: アニーリング実行の期間。

### 出力

  * `probabilities::Vector{Float64}`: ビット列に対する出力確率のベクトル。

### 注意事項

関数`schedule`は$[0, T]$から$[0, 1]$へのマッピングを行い、`schedule(0) == 0`、`schedule(T) == 1`である必要があります。最も単純な線形スケジュールの場合、`schedule(t) = t/T`と設定します。ドライバー$\hat H_D$と問題ハミルトニアン$\hat H_P$を用いると、完全なアニーリングハミルトニアンは次のように表されます。

$$
\hat H_A = (1 - t/T) \hat H_D + (t/T) \hat H_P
$$
