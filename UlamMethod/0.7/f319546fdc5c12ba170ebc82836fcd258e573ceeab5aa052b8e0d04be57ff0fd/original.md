```
counts(data, ulam_result)
```

Compute a vector `counts` such that `counts[i]` is equal to the number of points inside the ith bin and  `counts[end]` is the number of points outside the boundary (in nirvana).

```
counts(traj, ulam_result)
```

Compute `(counts(traj.x0, ulam_result), counts(traj.xT, ulam_result)`.
