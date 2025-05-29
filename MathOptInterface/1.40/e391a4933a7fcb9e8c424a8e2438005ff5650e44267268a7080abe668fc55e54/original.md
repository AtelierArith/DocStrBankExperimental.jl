```
INFEASIBILITY_CERTIFICATE::ResultStatusCode
```

An instance of the [`ResultStatusCode`](@ref) enum.

## About

The result vector is an infeasibility certificate.

If the [`PrimalStatus`](@ref) is [`INFEASIBILITY_CERTIFICATE`](@ref), then the primal result vector is a certificate of dual infeasibility.

If the [`DualStatus`](@ref) is [`INFEASIBILITY_CERTIFICATE`](@ref), then the dual result vector is a proof of primal infeasibility.
