```
model, classes = train_raster(cube::GItype, train::Union{Vector{<:GMTdataset}, String}; np::Int=0, density=0.1)
```

  * `cube`: 分類するためのバンドデータを持つキューブ。
  * `train`: モデルをトレーニングするために使用されるポリゴンを含むGMTデータセットのベクターまたはファイル名。注意: 各データセットには、クラス名を文字列として含む「class」という属性が関連付けられている必要があります。これは、セグメントが「>」記号で区切られたGMTマルチセグメントファイルの形式のテキストデータに対して、マルチセグメント区切り行にテキスト$Attrib(class=name)$が含まれている場合に達成できます。
  * `np`: $randinpolygon$によって決定されるポリゴンあたりのポイント数。
  * `density`: `np`の代替。$randinpolygon$関数のヘルプも参照してください。

トレーニングされたモデルとクラス名を返します。
