Definition of an analytic geometry function. This function maps reference coordinates to physical coordinates.

```c++
 [0,1]^\mathrm{dim} 
```

.

# Arguments

  * `cmesh`:[in] The cmesh.
  * `gtreeid`:[in] The global tree (of the cmesh) in which the reference point is.
  * `ref_coords`:[in] Array of dimension x *num_coords* many entries, specifying a point in
  * `num_coords`:[in]
  * `out_coords`:[out] The mapped coordinates in physical space of *ref_coords*. The length is *num_coords* * 3.
  * `tree_data`:[in] The data of the current tree as loaded by a t8*geom*load*tree*data_fn.
  * `user_data`:[in] The user data pointer stored in the geometry.
