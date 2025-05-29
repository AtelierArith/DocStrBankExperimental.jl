```
pointwise_logdensities(model::Model, chain::Chains, keytype = String)
```

Runs `model` on each sample in `chain` returning a `OrderedDict{String, Matrix{Float64}}` with keys corresponding to symbols of the variables, and values being matrices of shape `(num_chains, num_samples)`.

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

```jldoctest pointwise-logdensities-chains; setup=:(using Distributions)
julia> using MCMCChains

julia> @model function demo(xs, y)
           s ~ InverseGamma(2, 3)
           m ~ Normal(0, √s)
           for i in eachindex(xs)
               xs[i] ~ Normal(m, √s)
           end
           y ~ Normal(m, √s)
       end
demo (generic function with 2 methods)

julia> # Example observations.
       model = demo([1.0, 2.0, 3.0], [4.0]);

julia> # A chain with 3 iterations.
       chain = Chains(
           reshape(1.:6., 3, 2),
           [:s, :m]
       );

julia> pointwise_logdensities(model, chain)
OrderedDict{String, Matrix{Float64}} with 6 entries:
  "s"     => [-0.802775; -1.38222; -2.09861;;]
  "m"     => [-8.91894; -7.51551; -7.46824;;]
  "xs[1]" => [-5.41894; -5.26551; -5.63491;;]
  "xs[2]" => [-2.91894; -3.51551; -4.13491;;]
  "xs[3]" => [-1.41894; -2.26551; -2.96824;;]
  "y"     => [-0.918939; -1.51551; -2.13491;;]

julia> pointwise_logdensities(model, chain, String)
OrderedDict{String, Matrix{Float64}} with 6 entries:
  "s"     => [-0.802775; -1.38222; -2.09861;;]
  "m"     => [-8.91894; -7.51551; -7.46824;;]
  "xs[1]" => [-5.41894; -5.26551; -5.63491;;]
  "xs[2]" => [-2.91894; -3.51551; -4.13491;;]
  "xs[3]" => [-1.41894; -2.26551; -2.96824;;]
  "y"     => [-0.918939; -1.51551; -2.13491;;]

julia> pointwise_logdensities(model, chain, VarName)
OrderedDict{VarName, Matrix{Float64}} with 6 entries:
  s     => [-0.802775; -1.38222; -2.09861;;]
  m     => [-8.91894; -7.51551; -7.46824;;]
  xs[1] => [-5.41894; -5.26551; -5.63491;;]
  xs[2] => [-2.91894; -3.51551; -4.13491;;]
  xs[3] => [-1.41894; -2.26551; -2.96824;;]
  y     => [-0.918939; -1.51551; -2.13491;;]
```

## Broadcasting

Note that `x .~ Dist()` will treat `x` as a collection of *independent* observations rather than as a single observation.

```jldoctest; setup = :(using Distributions)
julia> @model function demo(x)
           x .~ Normal()
       end;

julia> m = demo([1.0, ]);

julia> ℓ = pointwise_logdensities(m, VarInfo(m)); first(ℓ[@varname(x[1])])
-1.4189385332046727

julia> m = demo([1.0; 1.0]);

julia> ℓ = pointwise_logdensities(m, VarInfo(m)); first.((ℓ[@varname(x[1])], ℓ[@varname(x[2])]))
(-1.4189385332046727, -1.4189385332046727)
```
