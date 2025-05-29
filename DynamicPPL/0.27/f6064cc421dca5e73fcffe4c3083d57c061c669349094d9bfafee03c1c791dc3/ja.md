```
generated_quantities(model::Model, parameters::NamedTuple)
generated_quantities(model::Model, values, keys)
generated_quantities(model::Model, values, keys)
```

`model`を実行し、変数`keys`を`values`に設定し、`model`が返す値を返します。

`NamedTuple`が与えられた場合、`keys=keys(parameters)`および`values=values(parameters)`です。

# 例

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

julia> parameters = (; s = 1.0, m_shifted=10);

julia> generated_quantities(model, parameters)
(0.0,)

julia> generated_quantities(model, values(parameters), keys(parameters))
(0.0,)
```
