```
f = transport_to(ν, μ)
```

Generates a [measurable function](https://en.wikipedia.org/wiki/Measurable_function) `f` that transforms a value `x` distributed according to measure `μ` to a value `y = f(x)` distributed according to a measure `ν`.

The [pushforward measure](https://en.wikipedia.org/wiki/Pushforward_measure) from `μ` under `f` is is equivalent to `ν`.

If terms of random values this implies that `f(rand(μ))` is equivalent to `rand(ν)` (if `rand(μ)` and `rand(ν)` are supported).

The resulting function `f` should support `ChangesOfVariables.with_logabsdet_jacobian(f, x)` if mathematically well-defined, so that densities of `ν` can be derived from densities of `μ` via `f` (using appropriate base measures).

Returns NoTransportOrigin{typeof(ν),typeof(μ)} if no transformation from `μ` to `ν` can be found.

To add transformation rules for a measure type `MyMeasure`, specialize

  * `MeasureBase.transport_def(ν::SomeStdMeasure, μ::CustomMeasure, x) = ...`
  * `MeasureBase.transport_def(ν::MyMeasure, μ::SomeStdMeasure, x) = ...`

and/or

  * `MeasureBase.transport_origin(ν::MyMeasure) = SomeMeasure(...)`
  * `MeasureBase.from_origin(μ::MyMeasure, x) = y`
  * `MeasureBase.to_origin(μ::MyMeasure, y) = x`

and ensure `MeasureBase.getdof(μ::MyMeasure)` is defined correctly.

A standard measure type like `StdUniform`, `StdExponential` or `StdLogistic` may also be used as the source or target of the transform:

```julia
f_to_uniform(StdUniform, μ)
f_to_uniform(ν, StdUniform)
```

Depending on [`getdof(μ)`](@ref) (resp. `ν`), an instance of the standard distribution itself or a power of it (e.g. `StdUniform()` or `StdUniform()^dof`) will be chosen as the transformation partner.
