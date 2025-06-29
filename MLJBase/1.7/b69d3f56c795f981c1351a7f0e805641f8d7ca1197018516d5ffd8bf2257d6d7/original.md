```
sampler(r::NominalRange, probs::AbstractVector{<:Real})
sampler(r::NominalRange)
sampler(r::NumericRange{T}, d)
```

Construct an object `s` which can be used to generate random samples from a `ParamRange` object `r` (a one-dimensional range) using one of the following calls:

```julia
rand(s)             # for one sample
rand(s, n)          # for n samples
rand(rng, s [, n])  # to specify an RNG
```

The argument `probs` can be any probability vector with the same length as `r.values`. The second `sampler` method above calls the first with a uniform `probs` vector.

The argument `d` can be either an arbitrary instance of `UnivariateDistribution` from the Distributions.jl package, or one of a Distributions.jl *types* for which `fit(d, ::NumericRange)` is defined. These include: `Arcsine`, `Uniform`, `Biweight`, `Cosine`, `Epanechnikov`, `SymTriangularDist`, `Triweight`, `Normal`, `Gamma`, `InverseGaussian`, `Logistic`, `LogNormal`, `Cauchy`, `Gumbel`, `Laplace`, and `Poisson`; but see the doc-string for [`Distributions.fit`](@ref) for an up-to-date list.

If `d` is an *instance*, then sampling is from a truncated form of the supplied distribution `d`, the truncation bounds being `r.lower` and `r.upper` (the attributes `r.origin` and `r.unit` attributes are ignored). For discrete numeric ranges (`T <: Integer`) the samples are rounded.

If `d` is a *type* then a suitably truncated distribution is automatically generated using `Distributions.fit(d, r)`.

*Important.* Values are generated with no regard to `r.scale`, except in the special case `r.scale` is a callable object `f`. In that case, `f` is applied to all values generated by `rand` as described above (prior to rounding, in the case of discrete numeric ranges).

### Examples

```julia-repl
julia> r = range(Char, :letter, values=collect("abc"))
julia> s = sampler(r, [0.1, 0.2, 0.7])
julia> samples =  rand(s, 1000);
julia> StatsBase.countmap(samples)
Dict{Char,Int64} with 3 entries:
  'a' => 107
  'b' => 205
  'c' => 688

julia> r = range(Int, :k, lower=2, upper=6) # numeric but discrete
julia> s = sampler(r, Normal)
julia> samples = rand(s, 1000);
julia> UnicodePlots.histogram(samples)
           ┌                                        ┐
[2.0, 2.5) ┤▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 119
[2.5, 3.0) ┤ 0
[3.0, 3.5) ┤▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 296
[3.5, 4.0) ┤ 0
[4.0, 4.5) ┤▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 275
[4.5, 5.0) ┤ 0
[5.0, 5.5) ┤▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 221
[5.5, 6.0) ┤ 0
[6.0, 6.5) ┤▇▇▇▇▇▇▇▇▇▇▇ 89
           └                                        ┘
```
