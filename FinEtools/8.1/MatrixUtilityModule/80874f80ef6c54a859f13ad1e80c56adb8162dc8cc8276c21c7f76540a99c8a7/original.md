```
vector_blocked_d(V, nfreedofs)
```

Extract the "data" part of a vector.

The vector is composed of two blocks

```
V = [V_f
     V_d]
```

Here `f` stands for free, and `d` stands for data (i.e. fixed, prescribed, ...).
