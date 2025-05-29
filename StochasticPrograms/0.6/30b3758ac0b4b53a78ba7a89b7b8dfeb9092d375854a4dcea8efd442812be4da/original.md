```
@scenario(args..., probability = )
```

Create [`Scenario`](@ref) matching some [`@uncertain`](@ref) declaration with a supplied probability.

```
@scenario(var1 = val1, var2 = val2, ..., probability = 1.0)
```

Create [`Scenario`](@ref) matching [`@uncertain`](@ref) annotation of the form `@uncertain var1, var2, ...`

```
@scenario(ξ[i=..., j=..., ...] = values, probability = 1.0)
```

Create [`Scenario`](@ref) matching [`@uncertain`](@ref) annotation of the form `@uncertain ξ[i=..., j=..., ...]`. `values` must have the same dimension as the specified index sets.

```
@scenario(ξ[i=..., j=..., ...], expr, probability = 1.0, requested_container = :Auto)
```

Create [`Scenario`](@ref) matching [`@uncertain`](@ref) annotation of the form `@uncertain ξ[i=..., j=..., ...]`. Wraps JuMP's `@container` macro to create `DenseAxisArray` or `SparseAxisArray` as underlying data. See `@container` for further syntax information.

## Examples

The following are equivalent ways of creating an instance of the random vector $[q₁(ξ) q₂(ξ) d₁(ξ) d₂(ξ)]$  of probability $0.4$ and values $[24.0 28.0 500.0 100.0]$.

```julia
@scenario q₁ = 24.0 q₂ = 28.0 d₁ = 500.0 d₂ = 100.0 probability = 0.4

@scenario ξ[i in 1:4] = [24.0, 28.0, 500.0, 100.0] probability = 0.4
```
