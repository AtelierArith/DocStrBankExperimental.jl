```
workpart(data::AbstractArray, workersel::AbstractVector{W}, current_worker::W) where {W}
```

実行ユニット `current_worker` が担当する `data` の部分を取得します。これは、`workersel` にリストされたワーカー間で `data` のパーティションを意味します。

一般的な `data` 配列に対して、`workpart` はビューを返します。もし `data` が `Range`（処理されるインデックスなど）の場合、サブレンジが返されます。

型 `W` は通常 `Int` であり、`workersel` は通常スレッド/プロセス ID の範囲/配列になります。

注意: `workersel` は昇順にソートされている必要があり、重複エントリを含んではいけません。

例:

```julia
using Distributed, Base.Threads
A = rand(100)
# ...
sub_A = workpart(A, workers(), myid())
# ...
idxs = workpart(eachindex(sub_A), allthreads(), threadid())
for i in idxs
    # ...
end
```
