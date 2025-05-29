```
set_prop!(g, prop, val)
set_prop!(g, v, prop, val)
set_prop!(g, e, prop, val)
set_prop!(g, s, d, prop, val)
```

Set (replace) property `prop` with value `val` in graph `g`, vertex `v`, or edge `e` (optionally referenced by source vertex `s` and destination vertex `d`). Will return false if vertex or edge does not exist, true otherwise.
