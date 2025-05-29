```
REDUCTION_CERTIFICATE::ResultStatusCode
```

An instance of the [`ResultStatusCode`](@ref) enum.

## About

The result vector is an ill-posed certificate; see [this article](https://arxiv.org/abs/1408.4685) for details.

If the [`PrimalStatus`](@ref) is [`REDUCTION_CERTIFICATE`](@ref), then the primal result vector is a proof that the dual problem is ill-posed.

If the [`DualStatus`](@ref) is [`REDUCTION_CERTIFICATE`](@ref), then the dual result vector is a proof that the primal is ill-posed.
