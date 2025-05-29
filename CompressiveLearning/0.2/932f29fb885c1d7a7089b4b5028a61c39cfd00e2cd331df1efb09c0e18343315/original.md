```julia
pca_inverse_problem(
    A,
    s,
    k;
    decoder,
    decoder_kwargs,
    out_dic
)

```

Generic decoding function for pca. Allows to select a decoding method via the keyword argument `decoder`.
