```
p4est_connectivity_new_brick(mi, ni, periodic_a, periodic_b)
```

A rectangular m by n array of trees with configurable periodicity. The brick is periodic in x and y if periodic_a and periodic_b are true, respectively.

### Prototype

```c
p4est_connectivity_t *p4est_connectivity_new_brick (int mi, int ni, int periodic_a, int periodic_b);
```
