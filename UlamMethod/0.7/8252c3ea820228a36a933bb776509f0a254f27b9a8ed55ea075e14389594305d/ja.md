```
membership(data, binner)
```

`Dim x N_points` の点の行列を取り、`memb[i] = j` の場合は `data[:,i]` が `binner.bins[j]` の中にあることを示し、`memb[i] = nothing` の場合は `data[:,i]` がどのビンにも入っていないことを示すベクトル `memb` を返します。

```
membership(data, ulam_result)
```

`membership(data, ulam_result.binner)` を計算します。

```
membership(traj, binner)
```

`(membership(traj.x0, binner), membership(traj.xT, binner))` を計算します。

```
membership(traj, ulam_result)
```

`membership(traj, ulam_result.binner)` を計算します。
