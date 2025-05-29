```
anneal(linear::AbstractDict, quad::AbstractDict; [, opts])
```

線形および二次バイアスによって表現される前向きイジング問題を解決します。

# 引数

  * `linear::Dict`: 磁場を意味する線形バイアス。
  * `quad::Dict`: スピン-スピン相互作用を意味する二次バイアス。

`opts` 辞書で提供できるオプション：

  * `:beta_min` - 逆温度の初期（最小）値。（デフォルト: 5.0）
  * `:beta_max` - 逆温度の最終（最大）値。（デフォルト: 15.0）
  * `:n_sweep` - `beta_min` と `beta_max` の間の分割数。（デフォルト: 1000）
  * `:n_read` - シミュレーテッドアニーリングの実行繰り返し回数。（デフォルト: 1）

# 例

```jldoctest
julia> using InverseIsing

julia> h = Dict(:a => 1) # フィールドバイアスを設定。

julia> J = Dict((:a, :b) => -1) # 相互作用を設定。

julia> response = anneal(h, J)

julia> response.sample
Dict{Symbol,Int64} with 2 entries:
  :a => 1
  :b => -1
```
