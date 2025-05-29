```
CartesianTopology(comm, dims)
```

N次元の直交トポロジーを、基盤のMPIコミュニケーター`comm`と次元`dims`を使用して作成します。`dims`のすべてのエントリが`0`でない場合、`dims`の積はMPIプロセスの総数`MPI.Comm_size(comm)`と等しくなる必要があります。`dims`のいずれか（またはすべて）のエントリが`0`の場合、対応する空間方向の次元は自動的に選択されます。
