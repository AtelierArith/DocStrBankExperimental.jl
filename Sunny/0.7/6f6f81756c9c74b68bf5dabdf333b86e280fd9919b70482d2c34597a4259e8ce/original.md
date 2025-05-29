```
to_inhomogeneous(sys::System)
```

Returns a copy of the system that allows for inhomogeneous interactions, which can be set using [`set_onsite_coupling_at!`](@ref), [`set_exchange_at!`](@ref), and [`set_vacancy_at!`](@ref).

Inhomogeneous systems do not support symmetry-propagation of interactions or system reshaping.
