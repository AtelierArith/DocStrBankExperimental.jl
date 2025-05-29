floatyx - 2D ImageMetaを2D float配列に変換（y x空間順序）

```
Usage:  (fimg, prop) = floatyx(img)

Argument:  img - ::ImageMeta{T,2}

Returns:  fimg - ::Array{Float64,2} "y" "x"空間順序で。
          prop - 入力画像のプロパティ辞書のコピー
                 "spatialorder"が調整された（必要な場合）。
```

ほとんどの画像処理関数は（行、列）形式の2D配列を期待し、ほとんどの特徴位置特定関数は（行、列）座標の形でコーナーおよびエッジ座標を返します。

この便利な関数は、2D ImageMetaを受け取り、データを抽出し、2D Float64配列に変換し、必要に応じてデータを転置して「y」「x」（行、列）空間順序にします。 ImageMetaの空間順序プロパティは["y","x"]に設定され、プロパティが返されます。
