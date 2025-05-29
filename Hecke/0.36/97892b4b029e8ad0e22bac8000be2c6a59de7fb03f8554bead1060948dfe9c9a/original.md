```
restrict_scalars(L::AbstractLat, K::QQField,
                                 alpha::FieldElem = one(base_field(L))) -> ZZLat
```

Given a lattice `L` in a space $(V, \Phi)$, return the $\mathcal O_K$-lattice obtained by restricting the scalars of $(V, \alpha\Phi)$ to the number field `K`. The rescaling factor $\alpha$ is set to 1 by default.

Note that for now one can only restrict scalars to $\mathbb Q$.
