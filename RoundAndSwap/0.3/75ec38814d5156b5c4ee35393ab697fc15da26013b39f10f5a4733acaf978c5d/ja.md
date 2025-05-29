```
スワップ
```

スワップを追跡するためのオブジェクト

# 引数:

  * `existing::Union{Symbol, Nothing}`: 既存の変数
  * `new::Union{Symbol, Nothing}`: 既存の変数を置き換える変数
  * `obj_value::Real`: このスワップの目的値
  * `success::Union{Bool, Nothing}`: スワップが成功したかどうか
  * `all_fixed::Union{Array{Symbol}, Nothing}`: swapper.to_consider で固定されたすべての変数
  * `termination_status::Union{String, TerminationStatusCode, Nothing}`: TerminationStatusCode
  * `solve_time::Union{Real, Nothing}`: 解決にかかる時間
  * `Swap(existing, new)`: Swapオブジェクトのコンストラクタ
