```
CVIProjection(; parameters...)
```

A structure representing the parameters for the Conjugate Variational Inference (CVI) projection method.  This structure is a subtype of `AbstractApproximationMethod` and is used to configure the settings for CVI.

CVI approximates the posterior distribution by projecting it onto a family of distributions with a conjugate form.

# Requirements

The `CVIProjection` method requires the `ExponentialFamilyProjection` package to be installed and loaded in the current environment with `using ExponentialFamilyProjection`.

# Parameters

  * `rng::R`: The random number generator used for sampling. Default is `Random.MersenneTwister(42)`.
  * `outsamples::S`: The number of samples used for approximating output message distributions. Default is `100`.
  * `out_prjparams::OF`: The form parameter used to specify the target distribution family for the output message.   If `nothing` (default), the form will be inferred from the marginal form.
  * `in_prjparams::IFS`: A NamedTuple-like object that specifies the target distribution family for each input edge.  Keys should be of the form `:in_k` where `k` is the input edge index. If `nothing` (default), the forms  will be inferred from the incoming messages.
  * `proposal_distribution::PD`: The proposal distribution used for generating samples. If not provided or set to  `nothing`, it will be inferred from incoming messages and automatically updated during iterations.
  * `sampling_strategy::SS`: The strategy for approximating the logpdf:

      * `FullSampling(n)`: Uses `n` samples drawn from distributions (default: `n=10`). Provides more accurate  approximation at the cost of increased computation time.
      * `MeanBased()`: Uses only the mean of each distribution as a single sample. Significantly faster but  less accurate for non-linear nodes or complex distributions.

# Examples

```julia
# Standard CVI projection with default settings
method = CVIProjection()

# Fast approximation using mean-based sampling
method = CVIProjection(sampling_strategy = MeanBased())

# Custom proposal with increased sample count
using Distributions
proposal = FactorizedJoint((NormalMeanVariance(0.0, 1.0), NormalMeanVariance(0.0, 1.0)))
method = CVIProjection(
    proposal_distribution = ProposalDistributionContainer(proposal),
    sampling_strategy = FullSampling(1000)
)

# Specify projection family for the output message
method = CVIProjection(out_prjparams = ProjectedTo(NormalMeanPrecision))

# Specify projection family for input edges
method = CVIProjection(in_prjparams = (in_1 = ProjectedTo(NormalMeanVariance), in_2 = ProjectedTo(GammaShapeRate)))
```

!!! note
    The `CVIProjection` method is an enhanced version of the deprecated `CVI`, offering better stability  and improved accuracy. Parameters and defaults may change as the implementation evolves.

