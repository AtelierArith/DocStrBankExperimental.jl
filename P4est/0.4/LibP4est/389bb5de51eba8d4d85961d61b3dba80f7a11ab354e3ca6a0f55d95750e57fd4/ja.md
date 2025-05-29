```
p4est_connectivity_new_brick(mi, ni, periodic_a, periodic_b)
```

可変周期の木の長方形 m x n 配列。brick は、periodic*a と periodic*b がそれぞれ真である場合、x および y で周期的です。

### プロトタイプ

```c
p4est_connectivity_t *p4est_connectivity_new_brick (int mi, int ni, int periodic_a, int periodic_b);
```
