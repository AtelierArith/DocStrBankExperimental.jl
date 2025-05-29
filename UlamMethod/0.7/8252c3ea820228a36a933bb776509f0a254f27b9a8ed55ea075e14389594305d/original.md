```
membership(data, binner)
```

Takes a `Dim x N_points` matrix of points and returns a vector `memb` where `memb[i] = j` if `data[:,i]` is  inside `binner.bins[j]` and `memb[i] = nothing` if `data[:,i]` is not inside any bin.

```
membership(data, ulam_result)
```

Compute `membership(data, ulam_result.binner)`.

```
membership(traj, binner)
```

Compute `(membership(traj.x0, binner), membership(traj.xT, binner))`.

```
membership(traj, ulam_result)
```

Compute `membership(traj, ulam_result.binner)`.
