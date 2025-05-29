```
get_traj(xyz::XYZ, ind = trues(xyz.traj.N))
```

Get trajectory data at specific indices.

**Arguments:**

  * `xyz`: `XYZ` flight data struct
  * `ind`: (optional) selected data indices

**Returns:**

  * `traj`: `Traj` trajectory struct at `ind`
