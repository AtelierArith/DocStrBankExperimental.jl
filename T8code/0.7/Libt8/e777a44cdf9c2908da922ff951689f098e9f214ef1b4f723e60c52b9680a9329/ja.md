```
t8_cmesh_new_hypercube_pad_ext(eclass, comm, boundary, polygons_x, polygons_y, polygons_z, periodic_x, periodic_y, periodic_z, use_axis_aligned, set_partition, offset)
```

### プロトタイプ

```c
t8_cmesh_t t8_cmesh_new_hypercube_pad_ext (const t8_eclass_t eclass, sc_MPI_Comm comm, const double *boundary, t8_locidx_t polygons_x, t8_locidx_t polygons_y, t8_locidx_t polygons_z, const int periodic_x, const int periodic_y, const int periodic_z, const int use_axis_aligned, const int set_partition, t8_gloidx_t offset);
```
