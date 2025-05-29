```
distributed_pinthreads(symbol;
    include_master = false,
    compact = false,
    nthreads_per_proc = Threads.nthreads(),
    kwargs...)
```

JuliaワーカーのJuliaスレッドを特定のドメイン（例：ソケット）にラウンドロビン方式で固定します。サポートされているドメイン（`symbol`）は `:sockets`、 `:numa`、および `:cores` です。

この関数を呼び出すと、すべてのJuliaワーカーのJuliaスレッドが指定されたドメイン間でラウンドロビン方式で分配され、ドメイン内のCPUスレッドの非重複範囲に固定されます。

異なるノードにホストされたJuliaワーカーを持つマルチノードセットアップがサポートされています。

`include_master=true` の場合、マスタープロセス（`Distributed.myid() == 1`）も固定されます。

`compact=false`（デフォルト）の場合、物理コアがハイパースレッドの前に占有されます。それ以外の場合、CPUコア - 複数のCPUスレッドを持つ可能性がある - が1つずつ埋められます（コンパクトピンニング）。

*例:*

```
using Distributed
addprocs(3)
@everywhere using ThreadPinning
distributed_pinthreads(:sockets)
```
