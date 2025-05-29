```
make_set_initial_state_from_file(ic_path, land::SoilCanopyModel{FT}) where {FT}
```

Returns a function which takes (Y,p,t0,land) as arguments, and updates the state Y in place with initial conditions from `ic_path`, a netCDF file. Fields in the cache `p` are used as pre-allocated memory and are updated as well, but this does not mean that the cache state is consitent with Y and t entirely.

Currently only tested and used for global simulations, but the same returned function should work for column simulations.

The returned function is a closure for `ic_path`. It could also be for `land`, as many other ClimaLand functions are, but we wish to preserve the argument `land` in `set_ic!` for users who wish to define their own initial condition function, which may require parameters, etc, stored in `land`.
