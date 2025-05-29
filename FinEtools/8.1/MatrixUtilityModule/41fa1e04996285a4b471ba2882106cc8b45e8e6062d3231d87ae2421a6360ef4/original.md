```
vector_blocked_f(V, nfreedofs)
```

Extract the "free" part of a vector.

The vector is composed of two blocks

```
V = [V_f
     V_d]
```

Here `f` stands for free, and `d` stands for data (i.e. fixed, prescribed, ...).
