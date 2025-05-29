```julia
GMM_inverse_problem(
    A,
    s,
    k;
    decoder,
    data_bounds,
    decoder_kwargs,
    rel_min_σ²,
    radX,
    mean_σ²,
    out_dic
)

```

Returns a pair (θ,α) of GMM parameters and weights matching the sketch `s`. Here θ is a d×k matrix whose columns are diracs, and α is a k-dimensional vector of weights.
