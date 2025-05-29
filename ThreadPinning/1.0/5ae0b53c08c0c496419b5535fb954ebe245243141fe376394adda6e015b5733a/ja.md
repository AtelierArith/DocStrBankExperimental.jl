```
mpi_pinthreads(symbol; compact, kwargs...)
```

MPIランクのJuliaスレッドを特定のドメイン（例：ソケット）にラウンドロビン方式で固定します。サポートされているドメイン（`symbol`）は`:sockets`、`:numa`、および`:cores`です。

この関数をすべてのMPIランクで呼び出すと、後者のJuliaスレッドは指定されたドメイン間でラウンドロビン方式で分配され、ドメイン内のCPUスレッドの非重複範囲に固定されます。

異なるノードにMPIランクがホストされるマルチノードセットアップがサポートされています。

`compact=false`（デフォルト）の場合、物理コアがハイパースレッドの前に占有されます。そうでない場合、CPUコア - 複数のCPUスレッドを持つ可能性がある - が1つずつ埋められます（コンパクトピンニング）。

*例:*

```
using ThreadPinning
using MPI
MPI.Init()
mpi_pinthreads(:sockets)
```
