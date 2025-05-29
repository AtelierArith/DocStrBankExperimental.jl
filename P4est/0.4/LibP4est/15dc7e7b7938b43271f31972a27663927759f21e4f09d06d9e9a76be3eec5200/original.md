```
p4est_quadrant_set_morton_ext128(quadrant, level, id)
```

Set quadrant Morton indices based on linear position given as [`p4est_lid_t`](@ref) in uniform grid. This is the inverse operation of p4est*quadrant*linear_id.

!!! note
    The user_data of *quadrant* is never modified.


### Parameters

  * `quadrant`:[in,out] Quadrant whose Morton indices will be set.
  * `level`:[in] Level of the grid and of the resulting quadrant.
  * `id`:[in] Linear index of the quadrant on a uniform grid.

### Prototype

```c
void p4est_quadrant_set_morton_ext128 (p4est_quadrant_t * quadrant, int level, const p4est_lid_t * id);
```
