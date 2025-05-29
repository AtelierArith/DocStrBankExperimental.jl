```
p8est_quadrant_linear_id_ext128(quadrant, level, id)
```

Computes the linear position as [`p8est_lid_t`](@ref) of a quadrant in a uniform grid. The grid and quadrant levels need not coincide. If they do, this is the inverse of p4est*quadrant*set_morton.

!!! note
    The user_data of *quadrant* is never modified.


### Parameters

  * `quadrant`:[in] Quadrant whose linear index will be computed. If the quadrant is smaller than the grid (has a higher quadrant->level), the result is computed from its ancestor at the grid's level. If the quadrant has a smaller level than the grid (it is bigger than a grid cell), the grid cell sharing its lower left corner is used as reference.
  * `level`:[in] The level of the regular grid compared to which the linear position is to be computed.
  * `id`:[in,out] A pointer to an allocated or static [`p8est_lid_t`](@ref). id will be the linear position of this quadrant on a uniform grid.

### Prototype

```c
void p8est_quadrant_linear_id_ext128 (const p8est_quadrant_t * quadrant, int level, p8est_lid_t * id);
```
