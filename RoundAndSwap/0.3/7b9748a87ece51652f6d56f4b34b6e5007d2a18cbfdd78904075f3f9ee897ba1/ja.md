```
swap(models::Array{Model}, consider_swapping::Array{VariableRef}; max_swaps = Inf, optimizer = nothing)
```

モデルと変数のリストを考慮して、目的関数を改善するために整数値を交換します。

# 引数:

  * `models`: 各スレッド用のモデルの配列
  * `consider_swapping`: 交換を考慮する変数の配列
  * `max_swaps`: 最大交換回数、デフォルトはInf
  * `save_path`: 各交換後にスワッパーを保存するためのパス、isnothing(save_path) ? 保存しない : 保存する、デフォルトはnothing
  * `auto_cpu_limit`: CPU時間制限を設定するかどうか。十分な実行可能および非実行可能な解が決定された場合、両者の解決時間に十分なギャップがあると、これを使用してCPU時間制限を設定します。
