```
propagate!(circ, psum::PauliSum{PauliStringType,NodePathProperties}; max_weight=Inf, max_freq=Inf, max_sins=Inf, customtruncfunc=nothing, kwargs...)
```

Construct a Pauli propagation surrogate of the propagated `PauliSum` through the circuit `circ` in the Heisenberg picture.  The `PauliSum` `psum` is modified in place. The circuit must only contain `CliffordGate`s and `PauliRotation`s.  It is applied to the Pauli sum in reverse order, and the action of each gate is its conjugate action. The input `psum` will be modified. Default truncations are `max_weight`, `max_freq`, and `max_sins`. A custom truncation function can be passed as `customtruncfunc` with the signature customtruncfunc(pstr::PauliStringType, coefficient)::Bool. Further `kwargs` are passed to the lower-level functions `applymergetruncate!`, `applytoall!`, `applyandadd!`, and `apply`.
