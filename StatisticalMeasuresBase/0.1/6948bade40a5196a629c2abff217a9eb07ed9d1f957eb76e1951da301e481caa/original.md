```
@combination SomeMeasure() = multimeasure(f)
@combination SomeMeasure() = multimeasure(f, mode=...)
```

Advanced tool for generating multiple measure constructors from a single scalar function, `(ŷ, y) -> f(ŷ, y)`. See "Enhancements" below for a variation for parameterized functions.

Assuming `f(yhat, y)` is an ordinary function with scalar arguments, the above calls acts as more-or-less as if `@combination` were absent, but with the following differences and additional actions:

*1.* A new concrete measure type `SomeMeasureOnScalars` is added: If `sm = SomeMeasureOnScalars()`, then `sm(yhat, y) = f(yhat, y)`.

*2.* Specifically, we have

```
SomeMeasure() = multimeasure(
    supports_missings_measure(sm),
    mode=mode,
) |> robust_measure |> fussy_measure
```

so that `missing` scalar elements are supported, relevant argument checks are performed, and weight arguments can be `nothing`.

*3.* An additional multi-target constructor is defined:

```
MultitargetSomeMeasure(; atomic_weights=nothing) = multimeasure(
    multimeasure(supports_missings_measure(sm), mode=mode),
    atomic_weights=atomic_weights,
    transform=vec∘collect,
) |> robust_measure |> fussy_measure
```

This measure will have similar support for `missing` scalar elements and `nothing` weights, and will perform argument checks. It can consume some kinds of tables.

*4.* The show method for displaying both kinds of measure is made friendlier; see   [`@fix_show`](@ref).

Note that, by construction, `measure = SomeMeasure()` if and only if `measure isa W{<:W<:W{<:W{<:SomeMeasureOnScalars}}}`, where `W = StatisticalMeasuresBase.Wrapper`, and `measure = MultitargetSomeMeasure(; atomic_weights=wts)` for some `wts` if and only if `measure isa W{<:W{<:W{<:W{<:W{<:SomeMeasureOnScalars}}}}}`.

# Enhancements

A single parameter can added to the provided expression, corresponding to the third argument of `f`. Traits may be also be declared, as they apply to `SomeMeasure`, which are appropriately lifted to `MultitargetSomeMeasure`, and dropped to `SomeScalarMeasure`.

Enhanced syntax example:

```
f(yhat, y, tol) = abs(yhat - y)/max(abs(y), tol)
@combination(
    ProportionalAbsoluteDifference(; tol=eps()) = multimeasure(f),
    observation_scitype = Continuous,     # becomes Union{Missing,Continuous}
    orientation=Loss(),
)
```

For further elucidation, see the documentation Tutorial.

!!! note
    This marcro is experimental and its behavior is subject to change in patch and minor releases.

