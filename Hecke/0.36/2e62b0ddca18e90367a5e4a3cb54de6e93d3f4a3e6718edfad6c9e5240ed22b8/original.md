```
restrict_scalars_with_map(L::AbstractLat, K::QQField,
                                          alpha::FieldElem = one(base_field(L)))
                                                    -> Tuple{ZZLat, AbstractSpaceRes}
```

Given a lattice `L` in a space $(V, \Phi)$, return the $\mathcal O_K$-lattice obtained by restricting the scalars of $(V, \alpha\Phi)$ to the number field `K`, together with the map `f` for extending scalars back. The rescaling factor $\alpha$ is set to 1 by default.

Note that for now one can only restrict scalars to $\mathbb Q$.
