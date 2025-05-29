```
init_T2(VAR::Int, T::Int)
init_T2{tp}(data::AbstractArray{tp,2})
```

initialize `t2_out` object for `T2!` either with number of variables `VAR` and observations/time steps `T` or with a two dimensional `data` matrix (time * variables)
