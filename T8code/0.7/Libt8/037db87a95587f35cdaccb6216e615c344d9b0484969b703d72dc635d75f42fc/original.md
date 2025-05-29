```
t8_geometry_jacobian(cmesh, gtreeid, ref_coords, num_coords, jacobian)
```

Evaluates the jacobian of a tree at a given reference point.

# Arguments

  * `cmesh`:[in] The cmesh
  * `gtreeid`:[in] The global id of the tree
  * `ref_coords`:[in] The reference coordinates at which to evaluate the jacobian
  * `num_coords`:[in] The number of reference coordinates
  * `jacobian`:[out] The jacobian at the reference coordinates

### Prototype

```c
void t8_geometry_jacobian (t8_cmesh_t cmesh, t8_gloidx_t gtreeid, const double *ref_coords, const size_t num_coords, double *jacobian);
```
