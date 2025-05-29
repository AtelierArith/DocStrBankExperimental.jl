```
Times(param; ns, Ns)
```

Constructs a mesh of times, to be used in initial-value problems (see `Problem`).

# Arguments

`param` is either

  * a `NamedTuple` containing `dt` the timestep and `T` the final time of comuptation; or
  * a vector of computed times.

## Optional keyword arguments

  * `ns`  : data are stored every `ns` computations (optional, default = 1).
  * `Ns`  : `Ns` data (in addition to the initial datum) are stored (optional, by default `floor( tfin/dt)).

If both `Ns` and `ns` are given, `Ns` overrules `ns`.

# Return values

`t=Times(args)` is of parametric type and offers

  * `t.Nc`: number of computed times (including initial datum);
  * `t.Ns`: number of stored times (including initial datum);
  * `t.ns`: number of computed times between two stored times;
  * `t.tfin`: the final time;
  * `t.dt`: the timestep;
  * `t.tc` : the vector of computed times;
  * `t.ts`: the vector of stored times.
