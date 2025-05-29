```
invariantmeasure(x::AbstractStateSpaceSet, binning::RectangularBinning;
    rng = Random.default_rng()) → iv::InvariantMeasure
```

Estimate an invariant measure over the points in `x` based on binning the data into rectangular boxes dictated by the `binning`, then approximate the transfer (Perron-Frobenius) operator over the bins. From the approximation to the transfer operator, compute an invariant distribution over the bins. Assumes that the input data are sequential.

Details on the estimation procedure is found the [`TransferOperator`](@ref) docstring.

## Example

```julia
using DynamicalSystems
henon_rule(x, p, n) = SVector{2}(1.0 - p[1]*x[1]^2 + x[2], p[2]*x[1])
henon = DeterministicIteratedMap(henon_rule, zeros(2), [1.4, 0.3])
orbit, t = trajectory(ds, 20_000; Ttr = 10)

# Estimate the invariant measure over some coarse graining of the orbit.
iv = invariantmeasure(orbit, RectangularBinning(15))

# Get the probabilities and bins
invariantmeasure(iv)
```

## Probabilities and bin information

```
invariantmeasure(iv::InvariantMeasure) → (ρ::Probabilities, bins::Vector{<:SVector})
```

From a pre-computed invariant measure, return the probabilities and associated bins. The element `ρ[i]` is the probability of visitation to the box `bins[i]`.

!!! hint "Transfer operator approach vs. naive histogram approach"
    Why bother with the transfer operator instead of using regular histograms to obtain probabilities?

    In fact, the naive histogram approach and the transfer operator approach are equivalent in the limit of long enough time series (as $n \to \intfy$), which is guaranteed by the ergodic theorem. There is a crucial difference, however:

    The naive histogram approach only gives the long-term probabilities that orbits visit a certain region of the state space. The transfer operator encodes that information too, but comes with the added benefit of knowing the *transition probabilities* between states (see [`transfermatrix`](@ref)).


See also: [`InvariantMeasure`](@ref).
