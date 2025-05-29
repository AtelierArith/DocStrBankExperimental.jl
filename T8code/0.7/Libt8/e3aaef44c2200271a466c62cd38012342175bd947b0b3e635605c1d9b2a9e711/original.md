```
t8_geometry_evaluate(cmesh, gtreeid, ref_coords, num_coords, out_coords)
```

Evaluates the geometry of a tree at a given reference point.

# Arguments

  * `cmesh`:[in] The cmesh
  * `gtreeid`:[in] The global id of the tree
  * `ref_coords`:[in] The reference coordinates at which to evaluate the geometry
  * `num_coords`:[in] The number of reference coordinates
  * `out_coords`:[out] The evaluated coordinates

### Prototype

```c
void t8_geometry_evaluate (t8_cmesh_t cmesh, t8_gloidx_t gtreeid, const double *ref_coords, const size_t num_coords, double *out_coords);
```
