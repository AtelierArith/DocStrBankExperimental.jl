```
REC!(rec_out::AbstractArray, D::AbstractArray, rec_threshold::Float64, temp_excl::Int = 0)
```

Memory efficient version of `REC()` for use within a loop. `rec_out` is preallocated output, should be initialised with `init_REC()`.
