```
rand(p::DiscreteHawkesProcess, steps)
```

離散ハークス過程からのランダムなイベントシーケンスをサンプリングします。

# 引数

  * `T::Int64`: サンプリングする時間ステップの数。

# 戻り値

  * `S::Array{Int64,2}`: イベントカウントの `N x T` 配列。
