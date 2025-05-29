```
struct VelocityExtension{A,B}
```

Wrapper to hold a stiffness matrix and a cache for the Hilbertian extension-regularisation. See Allaire et al. 2022 ([link](https://doi.org/10.1016/bs.hna.2020.10.004)).

The Hilbertian extension-regularisation method involves solving an  identification problem over a Hilbert space $H$ on $D$ with  inner product $\langle\cdot,\cdot\rangle_H$:  *Find* $g_\Omega\in H$ *such that* $\langle g_\Omega,w\rangle_H =-J^{\prime}(\Omega)(w\boldsymbol{n})~ \forall w\in H.$

This provides two benefits: 

1. It naturally extends the shape sensitivity from $\partial\Omega$  onto the bounding domain $D$; and
2. ensures a descent direction for $J(\Omega)$ with additional regularity  (i.e., $H$ as opposed to $L^2(\partial\Omega)$)

# Properties

  * `K::A`: The discretised inner product over $H$.
  * `cache::B`: Cached objects used for [`project!`](@ref)
