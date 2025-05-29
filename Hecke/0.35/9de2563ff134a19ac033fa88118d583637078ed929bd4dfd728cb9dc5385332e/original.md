```
restrict_scalars(L::AbstractLat, f::AbstractSpaceRes) -> ZZLat
```

Given a lattice `L` in a space $(V, \Phi)$ and a map `f` for restricting the scalars of $(V, \alpha\Phi)$ to a number field `K`, where $\alpha$ is in the base algebra of `L`, return the associated $\mathcal O_K$-lattice obtained from `L` with respect to `f`.

Note that for now one can only restrict scalars to $\mathbb Q$.
