```
init_UNIV(T::Int, VAR::Int)
init_UNIV{tp}(data::AbstractArray{tp, 2})
```

initialize a `univ_out` object to be used in `UNIV!()` either with number of time steps/observations `T` and variables `VAR` or with a `data` matrix observations * variables.
