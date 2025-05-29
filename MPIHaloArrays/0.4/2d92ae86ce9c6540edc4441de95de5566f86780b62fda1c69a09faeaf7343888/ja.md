```
CartesianTopology(comm::MPI.Comm, dims, periodicity; canreorder = false)
```

隣接情報、現在のランクなどを保持するCartesianTopology型を作成します。

# 引数

  * `dims`: 各方向のドメインの次元を設定するベクターまたはタプル。例えば、(4,3)は合計12のプロセスを意味し、x方向に4、y方向に3があります。
  * `periodicity`: 特定の次元に沿ってドメインが周期的かどうかを設定するブール値のベクターまたはタプル。

# 例

```julia

# 両方向に周期的境界を持つ4x4のトポロジーを作成
P = CartesianTopology((4,4), (true, true))
```
