```julia
random_GMM(
    k,
    d;
    separation,
    centers_var,
    inter_intra_var_ratio,
    Dirichlet_parameter,
    intra_var,
    intra_var_balance,
    out_dic
)

```

Returns a random mixture of `k` Gaussian in dimension `d`. Informations on the generation process can be obtained by passing a dictionary to the keyword argument `out_dic`.

Two of the following arguments can be simultaneously provided (the third being automatically computed):

  * `separation`: Gaussian centers are drawn according to a Normal distribution of standard deviation `separation × k^(1/d)`.
  * `intra_var`: variance of each component of the mixture (when `intra_var_balance` is set to 1.0).
  * `inter_intra_var_ratio`: ratio between inter-cluster and intra-cluster variances.

By default, a separation of 2.5 and an intra-variance of 1.0 will be used.

Other parameters include:

  * `Dirichlet_parameter`: controls the balance of the weights of the different clusters.
  * `intra_var_balance`: if greater than 1.0 (default value), random variances will be drawn between `intra_var` / `intra_var_balance` and `intra_var` × `intra_var_balance`.

See also: [`GMMDataset`](@ref).
