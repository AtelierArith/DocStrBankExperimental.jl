```
ids_snd, ids_rcv = assembly_local_indices(index_partition)
```

分散ベクトルのアセンブリにおいて、インデックスパーティション `index_partition` に定義された送信および受信されるローカルIDを返します。

`ids_snd[i]`（それぞれ `ids_rcv[i]`）のローカルインデックスに対応するローカル値は、部分 `neigs_snd[i]`（それぞれ `neigs_rcv[i]`）に送信されます。ここで、`neigs_snd, neigs_rcv = assembly_neighbors(index_partition)` です。
