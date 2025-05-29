```
searchbatch(index, Q, KNN::AbstractVector{KnnResult}; minbatch=0, pools=getpools(index)) -> indices, distances
```

指定されたインデックス内で、KnnResultの配列を使用してクエリのバッチを検索します。各KnnResultオブジェクトは異なる`k`値を指定できます。

# 引数

  * `minbatch`: 各スレッドで解決されるクエリの最小数。[`getminbatch`](@ref)を参照してください。
  * `pools`: 特殊なデータベースや距離関数に関連しています。ほとんどの場合、デフォルトを使用するだけで十分ですが、インデックスがクエリを解決するために他のインデックスを内部的に使用する場合は、異なるプールを使用する必要があります。これは、メモリアロケーションを減らすために使用される`Threads.nthreads()`の事前に割り当てられた`KnnResult`オブジェクトの配列である必要があります。
