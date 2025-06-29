```
imshow(img; kwargs...)
imshow(img, (minval, maxval); kwargs...)
```

次のいずれかによって定義された画像を描画します：

  * 有効なファイル名の画像を含む文字列。
  * 3次元の *H*×*W*×*C* 配列。これは *W* ピクセルの幅と *H* ピクセルの高さを持つ画像として描画され、*C* チャンネル（3または4）があり、RGBまたはRGBAの値が0から1の範囲に対応します。
  * 値の行列。これは、現在のカラーマップにおける相対的な位置に対応する色相で描画されます。カラーマップにマッピングされる値の範囲はデフォルトで `[0, 1]` ですが、`minval` と `maxval` の間の任意の範囲に設定できます。いずれかの制限を `nothing` に設定すると、データに基づいて自動的に決定されます。

# 例

```julia
# 画像を作成
x = LinRange(-3, 3, 150)
y = LinRange(-2, 2, 100)
# RGB 値
r = (1 .+ cos.(atan.(y, x')))/2
g = (1 .+ sin.(atan.(y, x')))/2
b = exp.(-(x'.^2 .+ y.^2)/4)
data = cat(r, g, b, dims=3)
# 画像を描画
imshow(data)

```
