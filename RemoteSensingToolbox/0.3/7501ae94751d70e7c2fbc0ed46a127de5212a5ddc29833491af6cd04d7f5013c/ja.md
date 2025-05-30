```
forward_mnf(transformation::MNF, raster, components::Int)
forward_mnf(transformation::MNF, signatures::Matrix, components::Int)
```

与えられたラスタまたは署名に対して前方最小ノイズ分数（MNF）回転を実行し、指定された数のコンポーネントのみを保持します。

# パラメータ

  * `transformation`: 以前に適合されたMNF変換。
  * `raster`: MNF変換を実行する`AbstractRaster`または`AbstractRasterStack`。
  * `signatures`: n x bのスペクトル署名の行列で、nは署名の数、bはバンドの数です。
  * `components`: 変換された画像に保持するバンドの数。この値を超えるすべてのバンド番号は破棄されます。
