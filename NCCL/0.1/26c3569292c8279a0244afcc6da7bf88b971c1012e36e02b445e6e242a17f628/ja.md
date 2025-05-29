```
NCCL.Communicator(nranks, rank; [unique_id]) :: Communicator
```

マルチスレッドまたはマルチプロセス環境で使用するための単一のコミュニケーターを作成します。`nranks`はコミュニケーター内のランクの数であり、`rank`は現在のランクの0ベースのインデックスです。`unique_id`はコミュニケーターのオプションの一意の識別子です。

# 例

```
comm = Communicator(length(CUDA.devices()), id, myid())
# これは他のすべてのランクが接続するまでブロックします
```

# 外部リンク

  * [`ncclCommInitRank`](https://docs.nvidia.com/deeplearning/nccl/user-guide/docs/api/comms.html#ncclCommInitRank)
