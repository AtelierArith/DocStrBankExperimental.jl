```julia
SavingCallback(save_func, saved_values::SavedValues;
    saveat = Vector{eltype(saved_values.t)}(),
    save_everystep = isempty(saveat),
    save_start = true,
    tdir = 1)
```

The saving callback lets you define a function `save_func(u, t, integrator)` which returns quantities of interest that shall be saved.

## Arguments

  * `save_func(u, t, integrator)` returns the quantities which shall be saved. Note that this should allocate the output (not as a view to `u`).
  * `saved_values::SavedValues` is the types that `save_func` will return, i.e. `save_func(t, u, integrator)::savevalType`. It's specified via `SavedValues(typeof(t),savevalType)`, i.e. give the type for time and the type that `save_func` will output (or higher compatible type).

## Keyword Arguments

  * `saveat` mimics `saveat` in `solve` from `solve`.
  * `save_everystep` mimics `save_everystep` from `solve`.
  * `save_start` mimics `save_start` from `solve`.
  * `save_end` mimics `save_end` from `solve`.
  * `tdir` should be `sign(tspan[end]-tspan[1])`. It defaults to `1` and should be adapted if `tspan[1] > tspan[end]`.

The outputted values are saved into `saved_values`. Time points are found via `saved_values.t` and the values are `saved_values.saveval`.
