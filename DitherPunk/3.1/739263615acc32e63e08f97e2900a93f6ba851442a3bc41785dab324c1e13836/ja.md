```
ErrorDiffusion(filter, offset)
```

一般化された誤差拡散アルゴリズム。色パレット `cs` を使用して `dither` を呼び出すと、ピクセルを反復処理し、`cs` 内の最も近い色に丸めます。丸め誤差は、整数 `offset` を中心とした行列 `filter` によって定義された近傍に「拡散」されます。

`dither` または `dither!` を誤差拡散法で使用する際には、キーワード引数 `clamp_error` を渡すことができ、デフォルトは `true` です。`true` の場合、各ピクセルの累積誤差は、最も近い色を検索する前に画像の色素タイプの制限内にクリンチされます。`clamp_error=false` に設定すると、グリッチ効果を得るために望ましい場合があります。

# 例

```julia-repl
julia> alg = FloydSteinberg() # ErrorDiffusion インスタンスを返す
ErrorDiffusion{Rational{Int64}, UnitRange{Int64}}(CartesianIndex{2}[CartesianIndex(1, 0), CartesianIndex(-1, 1), CartesianIndex(0, 1), CartesianIndex(1, 1)], Rational{Int64}[7//16, 3//16, 5//16, 1//16], (-1:1, 0:1))

julia> cs = ColorSchemes.PuOr_7  # ColorSchemes.jl を使用して色パレットプリセットを取得

julia> dither(img, alg, cs)

julia> dither(img, alg, cs; clamp_error=false)
```
