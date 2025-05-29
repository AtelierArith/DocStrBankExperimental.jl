```
extract_priors([rng::Random.AbstractRNG, ]model::Model)
```

Extract the priors from a model.

This is done by sampling from the model and recording the distributions that are used to generate the samples.

!!! warning
    Because the extraction is done by execution of the model, there are several caveats:

    1. If one variable, say, `y ~ Normal(0, x)`, where `x ~ Normal()` is also a random variable, then the extracted prior will have different parameters in every extraction!
    2. If the model does *not* have static support, say, `n ~ Categorical(1:10); x ~ MvNormmal(zeros(n), I)`, then the extracted priors themselves will be different between extractions, not just their parameters.

    Both of these caveats are demonstrated below.


# Examples

## Changing parameters

```jldoctest
julia> using Distributions, StableRNGs

julia> rng = StableRNG(42);

julia> @model function model_dynamic_parameters()
           x ~ Normal(0, 1)
           y ~ Normal(x, 1)
       end;

julia> model = model_dynamic_parameters();

julia> extract_priors(rng, model)[@varname(y)]
Normal{Float64}(μ=-0.6702516921145671, σ=1.0)

julia> extract_priors(rng, model)[@varname(y)]
Normal{Float64}(μ=1.3736306979834252, σ=1.0)
```

## Changing support

```jldoctest
julia> using LinearAlgebra, Distributions, StableRNGs

julia> rng = StableRNG(42);

julia> @model function model_dynamic_support()
           n ~ Categorical(ones(10) ./ 10)
           x ~ MvNormal(zeros(n), I)
       end;

julia> model = model_dynamic_support();

julia> length(extract_priors(rng, model)[@varname(x)])
6

julia> length(extract_priors(rng, model)[@varname(x)])
9
```
