```
Architectures.Arch(backend::Backend, comm::MPI.Comm, dims; device_id=nothing, gpu_aware=true)
```

バックエンド `backend` と `comm` を使用して分散アーキテクチャを作成します。GPU バックエンドの場合、デバイスはノード内のプロセス ID に基づいて自動的に選択されますが、`device_id` で指定することもできます。

# 引数

  * `backend::Backend`: アーキテクチャに使用するバックエンド。
  * `comm::MPI.Comm`: アーキテクチャに使用する MPI コミュニケーター。
  * `dims`: アーキテクチャの次元。

# キーワード引数

  * `device_id`: 使用するデバイスの ID。指定しない場合は、トポロジーの共有ランクに 1 を加えたものが使用されます。
  * `gpu_aware`: MPI 実装が GPU 対応かどうか。指定しない場合はデフォルトで `true` になります。互換性のあるバックエンドにのみ適用されます。
