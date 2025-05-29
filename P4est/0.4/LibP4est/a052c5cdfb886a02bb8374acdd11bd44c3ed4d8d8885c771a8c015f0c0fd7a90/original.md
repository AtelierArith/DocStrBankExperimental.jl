```
p4est_find_corner_transform(connectivity, itree, icorner, ci)
```

Fills an array with information about corner neighbors.

### Parameters

  * `itree`:[in] The number of the originating tree.
  * `icorner`:[in] The number of the originating corner.
  * `ci`:[in,out] A `p4est_corner_info_t` structure with initialized array.

### Prototype

```c
void p4est_find_corner_transform (p4est_connectivity_t * connectivity, p4est_topidx_t itree, int icorner, p4est_corner_info_t * ci);
```
