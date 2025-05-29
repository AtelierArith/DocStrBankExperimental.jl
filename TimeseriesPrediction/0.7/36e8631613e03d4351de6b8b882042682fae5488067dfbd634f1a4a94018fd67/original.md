```
Rotation <: Symmetry
```

Index sets at equal distance from the center point are equivalent, for the given input dimensions. E.g. for `Rotation(1,3)` and given center point `u[i,j,k,...]` all indices `m, n` that satisfy

```
|i-m|^2 + |k-n|^2 = r^2
```

for a given `r`, are equivalent. The same process generalizes to any number of input dimensions.
