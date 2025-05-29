```
duplicatesignals(x, n, k[, noise=false, t=1])
```

信号 `x` を与えると、各信号が `k` の倍数だけシフトされた `n` 個のシフトバージョンを返します。

`noise = true` に設定すると、μ = 0、σ² = t のランダムに生成されたガウスノイズが円形にシフトされた信号に追加されます。

# 引数

  * `x::AbstractVector{T} where T<:Number`: 複製される1D信号。
  * `n::Integer`:: 複製される信号の数。
  * `k::Integer`:: 各複製信号の円形シフトサイズ。
  * `noise::Bool`: (デフォルト: `false`) ガウスノイズを追加するかどうか。
  * `t::Real`: (デフォルト: 1) ノイズの相対的な大きさ。

# 戻り値

`::Array{T}`: 複製された信号。

# 例

```@repl
using WaveletsExt

x = generatesignals(:blocks)
duplicatesignals(x, 5, 0)      # [x x x x x]
```

*関連項目:* [`generatesignals`](@ref)
