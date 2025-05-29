```
CartesianTopology(comm::MPI.Comm, periodicity::Bool; canreorder = false)
```

与えられた境界周期性のベクトルのみでCartesianTopologyを作成します。これにより、ユーザーのための最適なサブドメインの順序付けが見つかります。
