```
AbstractPullback{NNLT<:NetworkLoss}
```

`AbstractPullback` is an `abstract type` that encompasses all ways of performing differentiation (especially computing the gradient with respect to neural network parameters) in `GeometricMachineLearning`.

If a user wants to implement a custom `Pullback` the following two functions have to be extended:

```julia
(_pullback::AbstractPullback)(ps, model, input_nt_output_nt::Tuple{<:QPTOAT, <:QPTOAT})
(_pullback::AbstractPullback)(ps, model, input_nt::QPT)
```

based on the `loss::NetworkLoss` that's stored in `_pullback`. The output of _pullback needs to be a `Tuple` that contains:

1. the `loss` evaluated at `ps` and `input_nt` (or `input_nt_output_nt`),
2. the gradient of `loss` with respect to `ps` that call be called with e.g.:

```julia
_pullback(ps, model, input_nt)[2](1) # returns the gradient wrt to `ps`
```

$\ldots$ we use this convention as it is analogous to how `Zygote` builds pullbacks.

An example is `GeometricMachineLearning.ZygotePullback`.
