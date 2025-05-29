```
V_sub = subtract_horizontalmean(V::AbstractArray{T, 3}; Percentage=false)
```

Subtracts the horizontal average of the 3D data array V.

If `Percentage=true`, the result is given as percentage; otherwise absolute values are returned
