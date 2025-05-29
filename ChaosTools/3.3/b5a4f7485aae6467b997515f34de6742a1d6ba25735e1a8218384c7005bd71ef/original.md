```
produce_orbitdiagram(ds::CoupledODEs, P, args...; kwargs...)
```

Shortcut function for producing an orbit diagram for a `CoupledODEs`. The function simply transforms `ds` to either a [`PoincareMap`](@ref) or a [`StroboscopicMap`](@ref), based on `P`, and then calls [`orbitdiagram](@ref)`(map, args...; kwargs...)`.

If `P isa Union{Tuple, Vector}` then a [`PoincareMap`](@ref) is created with `P` as the `plane`. If `P isa Real`, then a [`StroboscopicMap`](@ref) is created with `P` the period.

See [^DatserisParlitz2022] chapter 4 for a discussion on why making a map is useful.

[^DatserisParlitz2022]: Datseris & Parlitz 2022, *Nonlinear Dynamics: A Concise Introduction Interlaced with Code*, [Springer Nature, Undergrad. Lect. Notes In Physics](https://doi.org/10.1007/978-3-030-91032-7)
