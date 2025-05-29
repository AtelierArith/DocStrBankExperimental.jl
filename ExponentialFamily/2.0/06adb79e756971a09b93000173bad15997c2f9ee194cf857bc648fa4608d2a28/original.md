```
ExponentialFamilyDistribution(::Type{T}, naturalparameters, conditioner, attributes)
```

`ExponentialFamilyDistribution` structure represents a generic exponential family distribution in natural parameterization. Type `T` can be either a distribution type (e.g. from the `Distributions.jl` package) or a variate type (e.g. `Univariate`). In the context of the package, exponential family distributions are represented in the form:

$$
pₓ(x ∣ η) = h(x) ⋅ exp[ η ⋅ T(x) - A(η) ]
$$

Here:

  * `h(x)` is the base measure.
  * `T(x)` represents sufficient statistics.
  * `A(η)` stands for the log partition.
  * `η` denotes the natural parameters.

For a given member of exponential family: 

  * `getattributes` returns either `nothing` or `ExponentialFamilyDistributionAttributes`.
  * `getbasemeasure` returns a positive a valued function.
  * `getsufficientstatistics` returns an iterable of functions such as [x, x^2] or [x, logx].
  * `getnaturalparameters` returns an iterable holding the values of the natural parameters.
  * `getlogpartition` return a function that depends on the naturalparameters and it ensures that the distribution is normalized to 1.
  * `getsupport` returns the set that the distribution is defined over. Could be real numbers, positive integers, 3d cube etc. Use ither the `∈` operator or the `insupport()` function to check if a value belongs to the support.

!!! note
    The `attributes` can be `nothing`. In which case the package will try to derive the corresponding attributes from the type `T`.


```jldoctest
julia> ef = convert(ExponentialFamilyDistribution, Bernoulli(0.5))
ExponentialFamily(Bernoulli)

julia> getsufficientstatistics(ef)
(identity,)
```

```jldoctest
julia> ef = convert(ExponentialFamilyDistribution, Laplace(1.0, 0.5))
ExponentialFamily(Laplace, conditioned on 1.0)

julia> logpdf(ef, 4.0)
-6.0
```

See also: [`getbasemeasure`](@ref), [`getsufficientstatistics`](@ref), [`getnaturalparameters`](@ref), [`getlogpartition`](@ref), [`getsupport`](@ref)
