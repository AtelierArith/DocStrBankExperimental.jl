```
MPIWorkerManager([nprocs])
```

[`ClusterManager`](https://docs.julialang.org/en/v1/stdlib/Distributed/#Distributed.ClusterManager)は、MPI.jlランチャー[`mpiexec`](https://juliaparallel.github.io/MPI.jl/stable/environment/#MPI.mpiexec)を使用します。

ワーカーはすべてMPIセッションに属し、MPI操作を使用して通信できます。`MPIManager`とは異なり、MPIセッションは初期化されないため、ワーカーは`MPI.Init()`を実行する必要があります。

マスタープロセス（pid 1）はセッションの一部ではなく、TCP/IPを介してワーカーと通信します。

# 使用法

```
using Distributed, MPIClusterManager

mgr = MPIWorkerManager(4) # 4つのMPIワーカーを起動
mgr = MPIWorkerManager() # デフォルトの数のMPIワーカーを起動（`mpiexec`によって決定される）

addprocs(mgr; kwoptions...)
```

次の`kwoptions`がサポートされています：

  * `dir`: ワーカーの作業ディレクトリ。
  * `mpiexec`: MPIランチャー実行可能ファイル（デフォルト：MPI.jlからのランチャーを使用）
  * `mpiflags`: `mpiexec`に渡す追加のフラグ
  * `exename`: ワーカー上のJulia実行可能ファイル。
  * `exeflags`: Julia実行可能ファイルに渡す追加のフラグ。
  * `threadlevel`: MPIを初期化するためのスレッドレベル。詳細については

[`MPI.Init()`](https://juliaparallel.github.io/MPI.jl/stable/environment/#MPI.Init)を参照してください。

  * `topology`: ワーカーが互いに接続する方法。
  * `enable_threaded_blas`: ワーカーがスレッド化されたBLASを使用するかどうか。
  * `master_tcp_interface`: リッスンするサーバーインターフェース。これにより、指定されたインターフェースと同じネットワーク上の他のホストからの直接接続が可能になります（そうでない場合、`localhost`からの接続のみが許可されます）。
