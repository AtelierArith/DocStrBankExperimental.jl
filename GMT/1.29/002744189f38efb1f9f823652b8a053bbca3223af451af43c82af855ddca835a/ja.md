```
I2 = imfill(I; conn=4, is_transposed=true, layout="TRBa")
```

グレースケールの $GMTimage$ I または UInt8 行列 I の穴を埋めます。

ここで、穴は明るいピクセルに囲まれた暗いピクセルの領域として定義されます。

### 引数

  * `I::Union{GMTimage{UInt8, 2}, GMTimage{Bool, 2}, Matrix{UInt8}, Matrix{Bool}, BitMatrix}`: 入力画像。

### キーワード引数

  * `conn::Int`: 画像の埋め込みの接続性 (4 または 8)。デフォルトは 4。
  * `is_transposed::Bool`: `true` の場合、入力画像配列が転置されていることを示します。デフォルトは `true`。通常、$GMTimage$ は転置に関する情報を持っており（レイアウトが "TRB" の場合は `true`）、列優先順序で行列を渡す場合（Julia のデフォルト）、`is_transposed` は `false` に設定する必要があります。注意: デフォルトは `true` であり、これは $gmtread$ または $gdalread$ でファイル画像を読み込む際の通常のケースです。
  * `layout::String`: 入力行列のレイアウト（デフォルトは "TRBa"）。入力が GMTimage の場合、この引数は自動的に設定され、通常は無視できます。

### 戻り値

  * 穴が埋められた新しい $GMTimage$（または行列）。

### 例

```julia
# Matlab imfill からの例
I = gmtread("TESTSDIR * "assets/coins.png");
Ibw = binarize(I);
BW2 = imfill(Ibw);
```
