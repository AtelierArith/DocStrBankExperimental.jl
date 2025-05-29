```
datasetinfo(datasetpath; onlywithlabels = [], shufflelabels = [], rng = Random.GLOBAL_RNG)
```

ディスク上のデータセットサイズを表示し、最初の要素が選択されたIDのベクター、2番目の要素がラベルのDataFrameまたは何もないもの、3番目の要素がバイト単位の総サイズのタプルを返します。

# 引数

  * `onlywithlabels` は、フィルターとして使用するラベルとその値を指定することによって、ロードするデータセットの部分を選択するために使用されます。詳細については [`loaddataset`](@ref) を参照してください。
  * `shufflelabels` は、シャッフルするラベルの名前の `AbstractVector` です（デフォルト = []、シャッフルなしを意味します）。
  * `rng` は、シャッフル時に使用される乱数生成器です（再現性のため）；`Integer`（`MersenneTwister` のシードとして使用）または `AbstractRNG` のいずれかです。
