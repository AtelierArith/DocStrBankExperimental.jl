# 拡張ヘルプ

```
rand(::Type{VPolygon}; [N]::Type{<:Real}=Float64, [dim]::Int=2,
     [rng]::AbstractRNG=GLOBAL_RNG, [seed]::Union{Int, Nothing}=nothing)
```

### 入力

  * `num_vertices` – （オプション、デフォルト: `-1`）ポリゴンの頂点の数（下記のコメントを参照）

### 注意事項

頂点の数は引数 `num_vertices` で制御できます。負の値の場合、範囲 `3:10` の中からランダムな数を選択します。

### アルゴリズム

私たちは、[ここ](https://stackoverflow.com/a/47358689)に記載されたアイデアに従い、[Valtr95](@citet)に基づいています。また、[こちら](http://cglab.ca/~sander/misc/ConvexGeneration/convex.html)に素晴らしいビデオもあります。
