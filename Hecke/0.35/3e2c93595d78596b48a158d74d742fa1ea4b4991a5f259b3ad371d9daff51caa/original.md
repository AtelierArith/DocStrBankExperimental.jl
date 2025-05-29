```
is_isometric_with_isometry(V::QuadSpace, W::QuadSpace)
```

Returns whether $V$ and $W$ are isometric together with an isometry in case it exists. The isometry is given as an invertible matrix $T$ such that $T G_W T^t = G_V$, where $G_V$, $G_W$ are the Gram matrices.
