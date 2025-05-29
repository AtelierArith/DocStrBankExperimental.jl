```
NLPEvaluator(
    model::Model,
    _differentiation_backend::MOI.Nonlinear.AbstractAutomaticDifferentiation =
        MOI.Nonlinear.SparseReverseMode(),
)
```

Return an [`MOI.AbstractNLPEvaluator`](@ref) constructed from `model`

!!! warning
    Before using, you must initialize the evaluator using [`MOI.initialize`](@ref).


## Experimental

These features may change or be removed in any future version of JuMP.

Pass `_differentiation_backend` to specify the differentiation backend used to compute derivatives.
