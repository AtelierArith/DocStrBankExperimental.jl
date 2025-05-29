```
V_sub = subtract_horizontalmean(V::AbstractArray{T, 2}; Percentage=false)
```

Subtracts the horizontal average of the 2D data array V.

If `Percentage=true`, the result is given as percentage; otherwise absolute values are returned
