```
logjoint(model::Model, θ)
```

確率的 `model` の変数 `θ` の対数結合確率を返します。

[`logprior`](@ref) と [`loglikelihood`](@ref) を参照してください。

# 例

```jldoctest; setup=:(using Distributions)
julia> @model function demo(x)
           m ~ Normal()
           for i in eachindex(x)
               x[i] ~ Normal(m, 1.0)
           end
       end
demo (generic function with 2 methods)

julia> # `NamedTuple` を使用。
       logjoint(demo([1.0]), (m = 100.0, ))
-9902.33787706641

julia> # `OrderedDict` を使用。
       logjoint(demo([1.0]), OrderedDict(@varname(m) => 100.0))
-9902.33787706641

julia> # 真実。
       logpdf(Normal(100.0, 1.0), 1.0) + logpdf(Normal(), 100.0)
-9902.33787706641
```
