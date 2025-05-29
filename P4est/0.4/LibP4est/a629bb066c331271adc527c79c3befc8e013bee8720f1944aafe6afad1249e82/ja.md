```
p8est_connectivity_new_brick(m, n, p, periodic_a, periodic_b, periodic_c)
```

m x n x p の配列で、periodic*a、periodic*b、periodic_c がそれぞれ真であれば、x、y、z に周期性があります。

### プロトタイプ

```c
p8est_connectivity_t *p8est_connectivity_new_brick (int m, int n, int p, int periodic_a, int periodic_b, int periodic_c);
```
