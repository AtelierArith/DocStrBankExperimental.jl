```
ResultStatusCode
```

An Enum of possible values for the [`PrimalStatus`](@ref) and [`DualStatus`](@ref) attributes.

The values indicate how to interpret the result vector.

## Values

### [`NO_SOLUTION`](@ref)

The result vector is empty.

### [`FEASIBLE_POINT`](@ref)

The result vector is a feasible point.

### [`NEARLY_FEASIBLE_POINT`](@ref)

The result vector is feasible if some constraint tolerances are relaxed.

### [`INFEASIBLE_POINT`](@ref)

The result vector is an infeasible point.

### [`INFEASIBILITY_CERTIFICATE`](@ref)

The result vector is an infeasibility certificate.

If the [`PrimalStatus`](@ref) is [`INFEASIBILITY_CERTIFICATE`](@ref), then    the primal result vector is a certificate of dual infeasibility.

If the [`DualStatus`](@ref) is [`INFEASIBILITY_CERTIFICATE`](@ref), then the    dual result vector is a proof of primal infeasibility.

### [`NEARLY_INFEASIBILITY_CERTIFICATE`](@ref)

The result satisfies a relaxed criterion for a certificate of infeasibility.

If the [`PrimalStatus`](@ref) is [`NEARLY_INFEASIBILITY_CERTIFICATE`](@ref),    then the primal result vector is a certificate of dual infeasibility.

If the [`DualStatus`](@ref) is [`NEARLY_INFEASIBILITY_CERTIFICATE`](@ref),    then the dual result vector is a proof of primal infeasibility.

### [`REDUCTION_CERTIFICATE`](@ref)

The result vector is an ill-posed certificate; see [this article](https://arxiv.org/abs/1408.4685)    for details.

If the [`PrimalStatus`](@ref) is [`REDUCTION_CERTIFICATE`](@ref), then the    primal result vector is a proof that the dual problem is ill-posed.

If the [`DualStatus`](@ref) is [`REDUCTION_CERTIFICATE`](@ref), then the    dual result vector is a proof that the primal is ill-posed.

### [`NEARLY_REDUCTION_CERTIFICATE`](@ref)

The result satisfies a relaxed criterion for an ill-posed certificate.

### [`UNKNOWN_RESULT_STATUS`](@ref)

The result vector contains a solution with an unknown interpretation. Check    the solver log for more details.

### [`OTHER_RESULT_STATUS`](@ref)

The result vector contains a solution with an interpretation not covered by    one of the statuses defined above. Check the solver log for more details.
