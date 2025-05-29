```
スワッパー
```

すべてのスワップを追跡するオブジェクト

# 引数:

  * `to_swap::Array{Swap}`: まだ行われていないスワップのリスト
  * `consider_swapping::Array{Symbol}`: スワップを考慮する変数
  * `completed_swaps::Union{Array{Array{Swap}}, Nothing}`: 完了したスワップ
  * `sense::OptimizationSense`: 最適化の感覚、MAXまたはMIN
  * `max_swaps::Real`: 完了する最大スワップ数
  * `number_of_swaps::Int`: 完了したスワップの数
  * `Swapper(to_swap, to_swap_with, model; max_swaps)`: コンストラクタ
