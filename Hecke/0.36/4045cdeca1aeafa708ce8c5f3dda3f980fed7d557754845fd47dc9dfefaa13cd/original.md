```
is_conductor(C::Hecke.ClassField, m::AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}, inf_plc::Vector{InfPlc}=InfPlc[]; check) -> AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}, Vector{InfPlc}
```

Checks if (m, inf_plc) is the conductor of the abelian extension corresponding to $C$. If `check` is `false`, it assumes that the given modulus is a multiple of the conductor. This is usually faster than computing the conductor.
