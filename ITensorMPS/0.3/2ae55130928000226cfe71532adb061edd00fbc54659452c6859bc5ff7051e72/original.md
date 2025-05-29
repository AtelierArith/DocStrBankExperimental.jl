```
expand(state::MPS, reference::MPO; alg="global_krylov", krylovdim=2, cutoff)
```

Given an MPS `state` and an MPO `reference`, returns an MPS which is equal to `state` (has fidelity 1 with state) but whose MPS basis is expanded to contain a portion of the basis of the Krylov space built by repeated applications of `reference` to `state` that is orthogonal to the MPS basis of `state`. The `reference` operator is applied to `state` `krylovdim` number of times, with a default of 2 which should give a good balance between reliability and performance. See [^global_expansion] for more details.

The cutoff is used to control the truncation of the expanded basis and defaults to half the precision of the scalar type of the input state, i.e. ~1e-8 for `Float64`.

!!! warning
    Users are not given many customization options just yet as we gain more experience on the right balance between efficacy of the expansion and performance in various scenarios, and default values and keyword arguments are subject to change as we learn more about how to best use the method.


[^global_expansion]: Time Dependent Variational Principle with Ancillary Krylov Subspace. Mingru Yang, Steven R. White, [arXiv:2005.06104](https://arxiv.org/abs/2005.06104)
