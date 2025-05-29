```
RobustAdaptiveMetropolis
```

Robust Adaptive Metropolis-Hastings (RAM).

This is a simple implementation of the RAM algorithm described in [^VIH12].

# Fields

  * `α`: target acceptance rate. Default: 0.234.
  * `γ`: negative exponent of the adaptation decay rate. Default: `0.6`.
  * `S`: initial lower-triangular Cholesky factor of the covariance matrix. If specified, should be convertible into a `LowerTriangular`. Default: `nothing`, which is interpreted as the identity matrix.
  * `eigenvalue_lower_bound`: lower bound on eigenvalues of the adapted Cholesky factor. Default: `0.0`.
  * `eigenvalue_upper_bound`: upper bound on eigenvalues of the adapted Cholesky factor. Default: `Inf`.

# Examples

The following demonstrates how to implement a simple Gaussian model and sample from it using the RAM algorithm.

```jldoctest ram-gaussian; setup=:(using Random; Random.seed!(1234);)
julia> using AdvancedMH, Distributions, MCMCChains, LogDensityProblems, LinearAlgebra

julia> # Define a Gaussian with zero mean and some covariance.
       struct Gaussian{A}
           Σ::A
       end

julia> # Implement the LogDensityProblems interface.
       LogDensityProblems.dimension(model::Gaussian) = size(model.Σ, 1)

julia> function LogDensityProblems.logdensity(model::Gaussian, x)
           d = LogDensityProblems.dimension(model)
           return logpdf(MvNormal(zeros(d),model.Σ), x)
       end

julia> LogDensityProblems.capabilities(::Gaussian) = LogDensityProblems.LogDensityOrder{0}()

julia> # Construct the model. We'll use a correlation of 0.5.
       model = Gaussian([1.0 0.5; 0.5 1.0]);

julia> # Number of samples we want in the resulting chain.
       num_samples = 10_000;

julia> # Number of warmup steps, i.e. the number of steps to adapt the covariance of the proposal.
       # Note that these are not included in the resulting chain, as `discard_initial=num_warmup`
       # by default in the `sample` call. To include them, pass `discard_initial=0` to `sample`.
       num_warmup = 10_000;

julia> # Sample!
       chain = sample(
            model,
            RobustAdaptiveMetropolis(),
            num_samples;
            chain_type=Chains, num_warmup, progress=false, initial_params=zeros(2)
        );

julia> isapprox(cov(Array(chain)), model.Σ; rtol = 0.2)
true
```

It's also possible to restrict the eigenvalues to avoid either too small or too large values. See p. 13 in [^VIH12].

```jldoctest ram-gaussian
julia> chain = sample(
           model,
           RobustAdaptiveMetropolis(eigenvalue_lower_bound=0.1, eigenvalue_upper_bound=2.0),
           num_samples;
           chain_type=Chains, num_warmup, progress=false, initial_params=zeros(2)
       );

julia> norm(cov(Array(chain)) - [1.0 0.5; 0.5 1.0]) < 0.2
true
```

# References

[^VIH12]: Vihola (2012) Robust adaptive Metropolis algorithm with coerced acceptance rate, Statistics and computing.
