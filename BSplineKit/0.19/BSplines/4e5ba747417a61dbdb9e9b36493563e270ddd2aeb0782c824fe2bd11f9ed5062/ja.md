```
BSplineBasis{k, T}
```

次数 `k` のスプラインとノット要素型 `T <: Real` のためのBスプライン基底。

基底はノットのセットとBスプラインの次数によって定義されます。

---

```
BSplineBasis(order::BSplineOrder{k}, ts::AbstractVector; augment = Val(true))
BSplineBasis(order::BSplineOrder{k}, ts::NTuple; augment = Val(true))
```

ブレークポイント `ts` を持つ次数 `k` のBスプライン基底を作成します。

`augment = Val(true)` の場合、ブレークポイントは「拡張」され、境界ノットの重複度は `k` になります。通常の `Vector` として渡された場合、入力が変更される可能性があることに注意してください。詳細については [`augment_knots!`](@ref) を参照してください。

# 例

```jldoctest BSplineBasis
julia> breaks = range(-1, 1; length = 21)
-1.0:0.1:1.0

julia> B = BSplineBasis(BSplineOrder(5), breaks)
24-element BSplineBasis of order 5, domain [-1.0, 1.0]
 knots: [-1.0, -1.0, -1.0, -1.0, -1.0, -0.9, -0.8, -0.7, -0.6, -0.5  …  0.5, 0.6, 0.7, 0.8, 0.9, 1.0, 1.0, 1.0, 1.0, 1.0]
```

最初と最後のノットは $k = 5$ 回繰り返されることに注意してください。

`augment = Val(false)` の場合、入力ブレークポイントはBスプライン基底のノット $t_i$ として変更されずに取られます。妥当な範囲は $[-0.6, 0.6]$ に制限されることに注意してください。範囲は常に $[t_k, t_{N + 1}]$ として定義され、ここで $N$ は基底の長さ（以下では $N = 16$）です。

```jldoctest BSplineBasis
julia> Bn = BSplineBasis(5, breaks, augment = Val(false))
16-element BSplineBasis of order 5, domain [-0.6, 0.6]
 knots: -1.0:0.1:1.0
```

# 静的サイズの基底

静的サイズ（コンパイル時にサイズが知られている）で基底を定義するには、ブレークポイント `ts` をタプルまたは `StaticArrays` パッケージの `SVector` として渡す必要があります：

```jldoctest
julia> breaks = (0.0, 0.1, 0.2, 0.6, 1.0);

julia> B = BSplineBasis(BSplineOrder(3), breaks)
6-element BSplineBasis of order 3, domain [0.0, 1.0]
 knots: [0.0, 0.0, 0.0, 0.1, 0.2, 0.6, 1.0, 1.0, 1.0]

julia> knots(B)
9-element StaticArraysCore.SVector{9, Float64} with indices SOneTo(9):
 0.0
 0.0
 0.0
 0.1
 0.2
 0.6
 1.0
 1.0
 1.0
```
