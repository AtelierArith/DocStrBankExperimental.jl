```
trace_lattice_with_isometry(H::AbstractLat{T};
                            alpha::FieldElem = one(base_field(H)),
                            beta::FieldElem = gen(base_field(H)),
                            order::Integer = 2) where T  -> ZZLat, QQMatrix
```

Given a lattice `H` which is either:

  * a $\mathbb Z$-lattice (i.e. of type `ZZLat`);
  * a hermitian lattice over a CM-extension $E/K$, where $E/\mathbb{Q}$ is defined by an irreducible monic polynomial $p$ with $p(0) = 1$

return the pair $(L, f)$ where $L$ is a $\mathbb{Z}$-lattice obtained as the trace lattice of $H$ [`restrict_scalars(::AbstractLat)`](@ref)) and $f$ is an isometry of $L$ given by:

  * the identity if $H$ is a `ZZLat` and `order == 1`;
  * the opposite of the identity if $H$ is a `ZZLat` and `order == 2`;
  * given by the multiplication by an element `beta` of norm 1 in $E$ otherwise.

Note that the optional argument `order` has no effect if `H` is not a $\mathbb Z$-lattice.

The choice of `alpha` corresponds to the choice of a rescaling of the form on $H$ for the trace construction using [`restrict_scalars`](@ref).

The choice of `beta` corresponds to the choice of an element of norm 1 in the base field of $H$, in the hermitian case, used to construct the isometry `f`.

Note that the isometry `f` computed is given by its action on the ambient space of the trace lattice of `H`.
