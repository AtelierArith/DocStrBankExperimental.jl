```
searchbatch(index, Q, k::Integer; minbatch=0, pools=GlobalKnnResult) -> indices, distances
```

指定されたインデックス内でクエリのバッチを検索します（k近傍を検索します）。

# 引数

  * `index`: 検索構造
  * `Q`: クエリのセット
  * `k`: 取得する近傍の数

# キーワード引数

  * `minbatch` は、スレッドごとに解決されるクエリの数を指定します。

      * 整数 $1 ≤ minbatch ≤ |Q|$ は有効な値です
      * 利用可能なコアの数に基づいてデフォルトの数を計算するには `minbatch=0` を設定します。
      * 並列処理を避けるには `minbatch=-1` を設定します。
  * `pools` 特殊なデータベースや距離関数に関連します。ほとんどの場合、デフォルトを使用するのが十分ですが、インデックスが内部で他のインデックスを使用してクエリを解決する場合は異なるプールを使用する必要があります。これは、メモリ割り当てを削減するために使用される `Threads.nthreads()` の事前に割り当てられた `KnnResult` オブジェクトの配列である必要があります。

注: indices と distances の i 番目の列は、`Q` の i 番目のクエリに対応します。注: 各列の最終的なインデックスは、検索プロセスが `k` 近傍を取得できなかった場合、`0` になる可能性があります。
