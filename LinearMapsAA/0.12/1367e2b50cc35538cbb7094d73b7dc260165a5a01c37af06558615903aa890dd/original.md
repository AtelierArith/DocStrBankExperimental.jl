```
 mul!(yv, AO::LinearMapAO, xv, α, β)
```

Fancy 5-arg multiply when `yv` and `xv` are each a `Vector` of AbstractArrays. Basically does `mul!(yv[i], A, xv[i], α, β)` for `i in 1:length(xv)`.
