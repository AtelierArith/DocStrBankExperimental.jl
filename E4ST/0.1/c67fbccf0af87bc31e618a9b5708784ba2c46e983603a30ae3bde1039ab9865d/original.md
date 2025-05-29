```
get_egen_gen(data, model, gen_idx)
```

Returns the total energy generation from a gen summed over all rep time. 

```
get_egen_gen(data, model, gen_idx, year_idx)
```

Returns the total energy generation from a gen summed over rep time for the given year. 

```
get_egen_gen(data, model, gen_idx, year_idx, hour_idx)
```

Returns the total energy generation from a gen for the given year and hour.  This is pgen*gen multiplied by the number of hours spent at that representative hour.  See [`get*hour_weight`](@ref) 

  * To use this to retieve the variable values after the model has been optimized, wrap the function with `value()` like this: `value.(get_egen_gen(args...))`.
