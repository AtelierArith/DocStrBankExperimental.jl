```
p8est_connectivity_refine(conn, num_per_edge)
```

Uniformly refine a connectivity. This is useful if you would like to uniformly refine by something other than a power of 2.

### Parameters

  * `conn`:[in] A valid connectivity
  * `num_per_edge`:[in] The number of new trees in each direction. Must use no more than P8EST*OLD*QMAXLEVEL bits.

### Returns

a refined connectivity.

### Prototype

```c
p8est_connectivity_t *p8est_connectivity_refine (p8est_connectivity_t * conn, int num_per_edge);
```
