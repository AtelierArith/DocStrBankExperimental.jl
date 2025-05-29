```julia
NyströmSkOp(
    m,
    X,
    ker;
    linop_type,
    sampling_type,
    ls_regularization,
    stability_shifting,
    use_falkon,
    out_dic
)

```

Creates a `NyströmSkOp` object using the (symmetric) kernel `k` and `m` points randomly sampled from the dataset `X` (samples = columns). It is strongly advised to use a kernel from the KernelFunctions package if efficiency is required.
