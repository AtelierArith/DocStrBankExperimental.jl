```
dump_state([IO=stdout], sol, t, idx; sigdigits=5)
```

Takes a Network solution `sol` and prints the state at `t` as well as the initial state of the specified component model to `IO` (defaults to `stdout`).

`idx` musst a valid component index, i.e. `VIndex` or `EIndex` without symbol specification.

```
dump_state(sol, 1.0, VIndex(4))
dump_state(sol, 1.0, EIndex(2))
```

See also: [`dump_initial_state`](@ref).
