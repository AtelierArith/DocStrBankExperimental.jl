```
pointwise_loglikelihoods(model::Model, chain::Chains, keytype = String)
```

Runs `model` on each sample in `chain` returning a `OrderedDict{String, Matrix{Float64}}` with keys corresponding to symbols of the observations, and values being matrices of shape `(num_chains, num_samples)`.

`keytype` specifies what the type of the keys used in the returned `OrderedDict` are. Currently, only `String` and `VarName` are supported.

# Notes

Say `y` is a `Vector` of `n` i.i.d. `Normal(μ, σ)` variables, with `μ` and `σ` both being `<:Real`. Then the *observe* (i.e. when the left-hand side is an *observation*) statements can be implemented in three ways:

1. using a `for` loop:

```julia
for i in eachindex(y)
    y[i] ~ Normal(μ, σ)
end
```

2. using `.~`:

```julia
y .~ Normal(μ, σ)
```

3. using `MvNormal`:

```julia
y ~ MvNormal(fill(μ, n), σ^2 * I)
```

In (1) and (2), `y` will be treated as a collection of `n` i.i.d. 1-dimensional variables, while in (3) `y` will be treated as a *single* n-dimensional observation.

This is important to keep in mind, in particular if the computation is used for downstream computations.

# Examples

## From chain

```julia-repl
julia> using DynamicPPL, Turing

julia> @model function demo(xs, y)
           s ~ InverseGamma(2, 3)
           m ~ Normal(0, √s)
           for i in eachindex(xs)
               xs[i] ~ Normal(m, √s)
           end

           y ~ Normal(m, √s)
       end
demo (generic function with 1 method)

julia> model = demo(randn(3), randn());

julia> chain = sample(model, MH(), 10);

julia> pointwise_loglikelihoods(model, chain)
OrderedDict{String,Array{Float64,2}} with 4 entries:
  "xs[1]" => [-1.42932; -2.68123; … ; -1.66333; -1.66333]
  "xs[2]" => [-1.6724; -0.861339; … ; -1.62359; -1.62359]
  "xs[3]" => [-1.42862; -2.67573; … ; -1.66251; -1.66251]
  "y"     => [-1.51265; -0.914129; … ; -1.5499; -1.5499]

julia> pointwise_loglikelihoods(model, chain, String)
OrderedDict{String,Array{Float64,2}} with 4 entries:
  "xs[1]" => [-1.42932; -2.68123; … ; -1.66333; -1.66333]
  "xs[2]" => [-1.6724; -0.861339; … ; -1.62359; -1.62359]
  "xs[3]" => [-1.42862; -2.67573; … ; -1.66251; -1.66251]
  "y"     => [-1.51265; -0.914129; … ; -1.5499; -1.5499]

julia> pointwise_loglikelihoods(model, chain, VarName)
OrderedDict{VarName,Array{Float64,2}} with 4 entries:
  xs[1] => [-1.42932; -2.68123; … ; -1.66333; -1.66333]
  xs[2] => [-1.6724; -0.861339; … ; -1.62359; -1.62359]
  xs[3] => [-1.42862; -2.67573; … ; -1.66251; -1.66251]
  y     => [-1.51265; -0.914129; … ; -1.5499; -1.5499]
```

## Broadcasting

Note that `x .~ Dist()` will treat `x` as a collection of *independent* observations rather than as a single observation.

```jldoctest; setup = :(using Distributions)
julia> @model function demo(x)
           x .~ Normal()
       end;

julia> m = demo([1.0, ]);

julia> ℓ = pointwise_loglikelihoods(m, VarInfo(m)); first(ℓ[@varname(x[1])])
-1.4189385332046727

julia> m = demo([1.0; 1.0]);

julia> ℓ = pointwise_loglikelihoods(m, VarInfo(m)); first.((ℓ[@varname(x[1])], ℓ[@varname(x[2])]))
(-1.4189385332046727, -1.4189385332046727)
```
