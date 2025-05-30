```
BlockJacobiPreconditioner
```

オーバーラッピング・シュワルツ前処理器。

### 属性

  * `nblocks::Int64`: パーティションまたはブロックの数。
  * `blocksize::Int64`: 各ブロックのサイズ。
  * `partitions::Vector{Vector{Int64}}``:`npart` パーティションがリストとして保存される
  * `cupartitions`: `partitions` がGPUに転送される
  * `lpartitions::Vector{Int64}``: 各パーティションの長さ。
  * `culpartitions::Vector{Int64}``: GPU上の各パーティションの長さ。
  * `blocks`: ブロック・ヤコビの密なブロック
  * `cublocks`: `Js` がGPUに転送される
  * `map`: ビューを構築するためのマッピングとしてのパーティション
  * `cumap`: `cumap` がGPUに転送される
  * `part`: Metisによって出力されたパーティショニング
  * `cupart`: `part` がGPUに転送される
