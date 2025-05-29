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

スケッチ `s` に一致する GMM パラメータと重みのペア (θ,α) を返します。ここで θ は d×k 行列で、その列はディラック関数であり、α は k 次元の重みベクトルです。
