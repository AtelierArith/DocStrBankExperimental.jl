```
NEARLY_INFEASIBILITY_CERTIFICATE::ResultStatusCode
```

An instance of the [`ResultStatusCode`](@ref) enum.

## About

The result satisfies a relaxed criterion for a certificate of infeasibility.

If the [`PrimalStatus`](@ref) is [`NEARLY_INFEASIBILITY_CERTIFICATE`](@ref), then the primal result vector is a certificate of dual infeasibility.

If the [`DualStatus`](@ref) is [`NEARLY_INFEASIBILITY_CERTIFICATE`](@ref), then the dual result vector is a proof of primal infeasibility.
