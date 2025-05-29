```
repeat_periodically_as_spiral(sys::System, counts::NTuple{3, Int}; k, axis)
```

指定された `counts` に従って、各システム軸に沿って [`System`](@ref) の磁気セルを複数回繰り返します。各システム画像のスピンは、伝播波ベクトル `k`（RLU単位）および回転 `axis`（グローバル直交座標系で）に従って回転します。これは、特別な場合の `k = [0, 0, 0]` における [`repeat_periodically`](@ref) と一致します。

エネルギー最小化波ベクトル `k` とスピン双極子配置を見つけるために、[`minimize_spiral_energy!`](@ref) も参照してください。

# 例

```julia
k = minimize_spiral_energy!(sys, axis; k_guess=randn(3))
repeat_periodically_as_spiral(sys, counts; k, axis)
```
