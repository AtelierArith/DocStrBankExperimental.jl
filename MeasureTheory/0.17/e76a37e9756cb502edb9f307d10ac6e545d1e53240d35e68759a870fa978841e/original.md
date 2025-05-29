```
@parameterized <declaration>
```

The <declaration> gives a measure and its default parameters, and specifies its relation to its base measure. For example,     @parameterized Normal(μ,σ) declares the `Normal` is a measure with default parameters `μ and σ`. The result is equivalent to

```
struct Normal{N,T} <: ParameterizedMeasure{N}
    par :: NamedTuple{N,T}
end
KeywordCalls.@kwstruct Normal(μ,σ)
Normal(μ,σ) = Normal((μ=μ, σ=σ))
```

See [KeywordCalls.jl](https://github.com/cscherrer/KeywordCalls.jl) for details on `@kwstruct`.
