```
Align(inner_layout :: AbstractLayout{2, Ptype}, angle :: Ptype = zero(Ptype))
```

Align the vertex positions of `inner_layout` so that the principal axis of the resulting layout makes an `angle` with the **x**-axis. Also automatically centers the layout origin to its center of mass (average node position).

Only supports two-dimensional inner layouts.
