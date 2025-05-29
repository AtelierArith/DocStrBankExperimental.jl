```
modular_init(K::AbsSimpleNumField, p::ZZRingElem) -> modular_env
modular_init(K::AbsSimpleNumField, p::Integer) -> modular_env
```

Given a number field $K$ and an ``easy'' prime $p$ (i.e. fits into an \code{Int} and is coprime to the polynomial discriminant), compute the residue class fields of the associated prime ideals above $p$. Returns data that can be used by \code{modular*proj} and \code{modular*lift}.
