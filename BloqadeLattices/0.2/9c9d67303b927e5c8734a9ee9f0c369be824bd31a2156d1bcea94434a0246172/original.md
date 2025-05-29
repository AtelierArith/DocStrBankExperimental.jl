```
MaskedGrid{T}
MaskedGrid(xs, ys, mask)
```

Masked square lattice contains 3 fields, the x-coordinates, y-coordinates and a mask. e.g. `MaskedGrid([0.0, 1.0, 3.0], [0.0, 2.0,6.0], Bool[1 0 0; 0 1 1; 0 1 0])` specifies the following lattice:

```
     y₁   y₂        y₃
     ↓    ↓         ↓
x₁ → ●    ⋅         ●
x₂ → ⋅    ●         ●

x₃ → ⋅    ●         ⋅
```
