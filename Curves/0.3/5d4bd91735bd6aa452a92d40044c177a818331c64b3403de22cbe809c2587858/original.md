```
concat(c1:: Curve, c2:: Curve; drop_dup=true, kwargs...)
```

Merges two curves.

Element type is inferred by promotion. Dulicate points are dropped by default, unless ˋdrop_dup=falseˋ is set. The output Curve is constructed using default settings, alternative settings can be passed to the Curve constructor using the ˋkwargs...ˋ
