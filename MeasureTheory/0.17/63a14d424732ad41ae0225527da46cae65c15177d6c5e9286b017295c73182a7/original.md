`asparams` build on `TransformVariables.as` to construct bijections to the parameter space of a given parameterized measure. Because this is only possible for continuous parameter spaces, we allow constraints to assign values to any subset of the parameters.

---

```
asparams(::Type{<:ParameterizedMeasure}, ::StaticSymbol)
```

Return a transformation for a particular parameter of a given parameterized measure. For example,

```
julia> asparams(Normal, static(:σ))
asℝ₊
```

---

```
asparams(::Type{<: ParameterizedMeasure{N}}, constraints::NamedTuple) where {N}
```

Return a transformation for a given parameterized measure subject to the named tuple `constraints`. For example,

```
julia> asparams(Binomial{(:p,)}, (n=10,))
TransformVariables.TransformTuple{NamedTuple{(:p,), Tuple{TransformVariables.ScaledShiftedLogistic{Float64}}}}((p = as𝕀,), 1)
```

---

```
aspararams(::ParameterizedMeasure)
```

Return a transformation with no constraints. For example,

```
julia> asparams(Normal{(:μ,:σ)})
TransformVariables.TransformTuple{NamedTuple{(:μ, :σ), Tuple{TransformVariables.Identity, TransformVariables.ShiftedExp{true, Float64}}}}((μ = asℝ, σ = asℝ₊), 2)
```
