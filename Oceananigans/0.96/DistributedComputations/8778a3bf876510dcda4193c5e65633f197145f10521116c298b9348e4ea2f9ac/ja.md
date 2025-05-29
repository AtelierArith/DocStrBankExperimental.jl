```
Distributed(child_architecture = CPU();
            partition = Partition(MPI.Comm_size(communicator)),
            devices = nothing,
            communicator = MPI.COMM_WORLD,
            synchronized_communication = false)
```

MPIを使用して通信を行う分散アーキテクチャを返します。

# 位置引数

  * `child_architecture`: 計算がCPUまたはGPUのどちらで行われるかを指定します。                       デフォルト: `CPU()`。

# キーワード引数

  * `partition`: `x`、`y`、および `z` 方向の総プロセッサを指定する [`Partition`](@ref)。              分散 `z` 方向のサポートは限られているため、              `z = 1` のキーワード引数を使用することを強くお勧めします。
  * `devices`: ローカルランクにリンクされた `GPU` デバイス。GPUは、            ローカルノードランクに基づいて `devices[node_rank]` のように割り当てられます。            `--ntasks-per-node` <= `--gres=gpu` を実行することを確認してください。            `nothing` の場合、デバイスは利用可能なリソースに基づいて自動的に割り当てられます。            `child_architecture = CPU()` の場合、この引数は無関係です。
  * `communicator`: ノード間のデータ転送を調整するMPIコミュニケーター。                 デフォルト: `MPI.COMM_WORLD`。
  * `synchronized_communication`: このキーワード引数は、下流のコードの動作を制御するために使用できます。                               `true` の場合、下流のコードはこのタグを使用して、                               ノード間の通信を「非同期的」に行うアルゴリズムと、                               通信と計算が「同期的」（すなわち、一つずつ実行される）である代替の直列アルゴリズムの間で切り替えることができます。                               デフォルト: `false`、サポートされている場合は非同期アルゴリズムの使用を指定し、                               これにより解決までの時間が短縮される可能性があります。
