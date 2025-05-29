```
p8est_partition_for_coarsening(p8est_, num_quadrants_in_proc)
```

Correct partition to allow one level of coarsening.

### Parameters

  * `p8est`:[in] forest whose partition is corrected
  * `num_quadrants_in_proc`:[in,out] partition that will be corrected

### Returns

absolute number of moved quadrants

### Prototype

```c
p4est_gloidx_t p8est_partition_for_coarsening (p8est_t * p8est, p4est_locidx_t * num_quadrants_in_proc);
```
