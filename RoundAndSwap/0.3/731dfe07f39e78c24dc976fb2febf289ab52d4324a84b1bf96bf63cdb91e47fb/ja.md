```
swap(model::Model, consider_swapping::Array{VariableRef}; optimizer = nothing, max_swaps = Inf,save_path::Union{Nothing, String}=nothing)
```

モデルと変数のリストを考慮して、整数値を入れ替えて目的関数を改善します。

# 引数:

  * `models`: 各スレッド用のモデルの配列
  * `consider_swapping`: 入れ替えを考慮する変数の配列
  * `optimizer`: 使用する特定のオプティマイザー、[Gurobi, Ipopt, HiGHS]にない場合
  * `max_swaps`: 最大入れ替え回数、デフォルトはInf
  * `save_path`: 各入れ替え後にスワッパーを保存するパス、isnothing(save_path) ? 保存しない : 保存する、デフォルトはnothing
