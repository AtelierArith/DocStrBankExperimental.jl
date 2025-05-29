```julia
GMM_dataset(k, d, n; center, out_dic, kwargs...)

```

Returns a dataset X whose  `n` columns are drawn w.r.t. a mixture of `k` Gaussians. Additional informations on the generation process can be obtained by passing a dictionary `out_dic`. See also: [`random_GMM`](@ref), to which keyword arguments are passed.
