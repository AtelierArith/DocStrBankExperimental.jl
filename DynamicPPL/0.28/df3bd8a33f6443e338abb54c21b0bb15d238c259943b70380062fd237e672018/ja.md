```
loglikelihood(model::Model, θ)
```

確率的 `model` に対する変数 `θ` の対数尤度を返します。

関連情報として [`logjoint`](@ref) と [`logprior`](@ref) を参照してください。

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
       loglikelihood(demo([1.0]), (m = 100.0, ))
-4901.418938533205

julia> # `OrderedDict` を使用。
       loglikelihood(demo([1.0]), OrderedDict(@varname(m) => 100.0))
-4901.418938533205

julia> # 真実。
       logpdf(Normal(100.0, 1.0), 1.0)
-4901.418938533205
```
