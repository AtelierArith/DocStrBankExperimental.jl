```
searchbatch(index, Q, I::AbstractMatrix{Int32}, D::AbstractMatrix{Float32}; minbatch=0, pools=getpools(index)) -> indices, distances
```

指定されたインデックス内でクエリのバッチを検索し、`I` と `D` を出力として返します（`k=size(I, 1)` の検索）。

# 引数

  * `index`: 検索構造
  * `Q`: クエリのセット
  * `k`: 取得する近傍の数

# キーワード引数

  * `minbatch`: 各スレッドごとに解決されるクエリの最小数、[`getminbatch`](@ref) を参照
  * `pools`: 特殊なデータベースや距離関数に関連します。ほとんどの場合、デフォルトを使用するだけで十分ですが、インデックスがクエリを解決するために他のインデックスを内部的に使用する場合は、異なるプールを使用する必要があります。これは、メモリ割り当てを減らすために使用される `Threads.nthreads()` の事前割り当てされた `KnnResult` オブジェクトの配列である必要があります。
