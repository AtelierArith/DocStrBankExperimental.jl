```
Marginal(data, is_clamped, is_initial, addons)
```

変分メッセージパッシングフレームワークにおけるマージナルの実装。

# 引数

  * `data::D`: マージナルは常にそれに関連付けられたデータオブジェクトを保持し、通常は確率分布です。
  * `is_clamped::Bool`: このマージナルが定数計算の結果であるかどうかを指定します（例：クランプされた定数）。
  * `is_initial::Bool`: このマージナルが初期化に使用されたかどうかを指定します。
  * `addons::A`: マージナルのアドオンを指定し、追加の情報（例：デバッグ情報、メモリなど）を持つことがあります。

# 例

```jldoctest
julia> distribution = Gamma(10.0, 2.0)
Distributions.Gamma{Float64}(α=10.0, θ=2.0)

julia> message = Marginal(distribution, false, true, nothing)
Marginal(Distributions.Gamma{Float64}(α=10.0, θ=2.0))

julia> mean(message) 
20.0

julia> getdata(message)
Distributions.Gamma{Float64}(α=10.0, θ=2.0)

julia> is_clamped(message)
false

julia> is_initial(message)
true
```
