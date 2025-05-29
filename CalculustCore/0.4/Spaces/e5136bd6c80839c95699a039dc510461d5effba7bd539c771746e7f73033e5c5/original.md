```
massOp(V::AbstractSpace, discr::AbstractDiscretization)
```

Mass Operator: ∫⋅dx

Represents the mass matrix for discretization scheme `discr`.

For a `Galerkin` discretization, the `[ij]`th entry corresponds to the inner product of the `i`th and `j`th basis functions.

$[M]_{ij} = \int_\Omega \phi_i(x)\phi_j(x) dx = \langle \phi_i, \phi_j \rangle$
