```
ref_add_core!(
    ref::Dict{Symbol,<:Any};
    kwargs...)
```

Populates the dictionary `ref`, which stores commonly-used, precomputed data. The function also converts data types, filters deactivated components, and stores values that are computed from systemwide analysis of the original input data. Some of the most important keys of this dictionary describe common network components, including:

  * `:pipe` – the set of pipes,
  * `:des_pipe` – the set of design pipes,
  * `:pump` – the set of pumps,
  * `:regulator` – the set of pressure regulating valves,
  * `:short_pipe` – the set of short pipes,
  * `:valve` – the set of gate and check valves,
  * `:node` – the set of nodes,
  * `:demand` – the set of demands,
  * `:reservoir` – the set of reservoirs,
  * `:tank` – the set of tanks
