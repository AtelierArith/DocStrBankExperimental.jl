```
p8est_connectivity_new_brick(m, n, p, periodic_a, periodic_b, periodic_c)
```

An m by n by p array with periodicity in x, y, and z if periodic_a, periodic_b, and periodic_c are true, respectively.

### Prototype

```c
p8est_connectivity_t *p8est_connectivity_new_brick (int m, int n, int p, int periodic_a, int periodic_b, int periodic_c);
```
