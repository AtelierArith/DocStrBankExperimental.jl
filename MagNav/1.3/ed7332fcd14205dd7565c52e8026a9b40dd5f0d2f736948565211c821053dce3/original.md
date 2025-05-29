```
get_igrf(xyz::XYZ, ind = trues(xyz.traj.N);
         frame::Symbol   = :body,
         norm_igrf::Bool = false,
         check_xyz::Bool = true)
```

Get the IGRF Earth vector in the body or navigation frame given an `XYZ` flight data struct containing trajectory information, valid indices, a start date in IGRF time (years since 0 CE), and reference frame.

**Arguments:**

  * `xyz`:       `XYZ` flight data struct
  * `ind`:       (optional) selected data indices
  * `frame`:     (optional) desired reference frame {`:body`,`:nav`}
  * `norm_igrf`: (optional) if true, normalize `igrf_vec`
  * `check_xyz`: (optional) if true, cross-check with `igrf` field in `xyz`

**Returns:**

  * `igrf_vec`: length-`N` stacked vector of `3` IGRF coordinates in `frame`
