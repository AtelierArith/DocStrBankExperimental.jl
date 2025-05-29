```
returned(model::Model, parameters::NamedTuple)
returned(model::Model, values, keys)
returned(model::Model, values, keys)
```

Execute `model` with variables `keys` set to `values` and return the values returned by the `model`.

If a `NamedTuple` is given, `keys=keys(parameters)` and `values=values(parameters)`.

# Example

```jldoctest
julia> using DynamicPPL, Distributions

julia> @model function demo(xs)
           s ~ InverseGamma(2, 3)
           m_shifted ~ Normal(10, √s)
           m = m_shifted - 10
           for i in eachindex(xs)
               xs[i] ~ Normal(m, √s)
           end
           return (m, )
       end
demo (generic function with 2 methods)

julia> model = demo(randn(10));

julia> parameters = (; s = 1.0, m_shifted=10.0);

julia> returned(model, parameters)
(0.0,)

julia> returned(model, values(parameters), keys(parameters))
(0.0,)
```
