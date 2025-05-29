```
restrict_scalars(V::AbstractSpace, K::QQField,
                                   alpha::FieldElem = one(base_ring(V)))
                                                -> QuadSpace, AbstractSpaceRes
```

Given a space $(V, \Phi)$ and a subfield `K` of the base algebra `E` of `V`, return the quadratic space `W` obtained by restricting the scalars of $(V, \alpha\Phi)$ to `K`, together with the map `f` for extending the scalars back. The form on the restriction is given by $Tr \circ \Phi$ where $Tr: E \to K$ is the trace form. The rescaling factor $\alpha$ is set to 1 by default.

Note that for now one can only restrict scalars to $\mathbb Q$.
