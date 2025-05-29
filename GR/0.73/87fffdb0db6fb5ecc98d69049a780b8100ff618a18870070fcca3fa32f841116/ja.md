```
drawimage(xmin::Real, xmax::Real, ymin::Real, ymax::Real, width::Int, height::Int, data, model::Int = 0)
```

指定された長方形の領域に画像を描画します。

**パラメータ:**

`xmin`, `ymin` :     長方形の最初の隅の点 `xmax`, `ymax` :     長方形の2番目の隅の点 `width`, `height` :     画像の幅と高さ `data` :     幅と高さで次元化された色値の配列 `model` :     カラーモデル (デフォルト=0)

利用可能なカラーモデルは次のとおりです:

```
+-----------------------+---+-----------+
|MODEL_RGB              |  0|   AABBGGRR|
+-----------------------+---+-----------+
|MODEL_HSV              |  1|   AAVVSSHH|
+-----------------------+---+-----------+
```

点 (`xmin`, `ymin`) と (`xmax`, `ymax`) は、長方形の対角にある隅のワールド座標を定義します。この長方形は `width` と `height` のセルに分割されます。2次元配列 `data` は各セルの色を指定します。
