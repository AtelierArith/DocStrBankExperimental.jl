```
power_series_ring(R::Ring, prec::Int, s::VarName; cached::Bool=true, model::Symbol=:capped_relative)
```

Return a tuple $(S, x)$ consisting of the parent object `S` of a power series ring over the given base ring and a generator `x` for the power series ring. The maximum precision of power series in the ring is set to `prec`. If the model is set to `:capped_relative` this is taken as a maximum relative precision, and if it is set to `:capped_absolute` this is take to be a maximum absolute precision. The supplied string `s` specifies the way the generator of the power series ring will be printed. By default, the parent object `S` will be cached so that supplying the same base ring, string and precision in future will return the same parent object and generator. If caching of the parent object is not required, `cached` can be set to `false`.
