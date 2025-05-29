```
OutcomeSpace
```

The supertype for all outcome space implementation.

## Description

In ComplexityMeasures.jl, an outcome space defines a set of possible outcomes $\Omega = \{\omega_1, \omega_2, \ldots, \omega_L \}$ (some form of discretization). In the literature, the outcome space is often also called an "alphabet", while each outcome is called a "symbol" or an "event".

An outcome space also defines a set of rules for mapping input data to to each outcome $\omega_i$, a processes called *encoding* or *symbolizing* or *discretizing* in the literature (see [encodings](@ref encodings)). Some [`OutcomeSpace`](@ref)s first apply a transformation, e.g. a delay embedding, to the data before discretizing/encoding, while other [`OutcomeSpace`](@ref)s discretize/encode the data directly.

## Implementations

| Outcome space                           | Principle                         | Input data                | Counting-compatible |
|:--------------------------------------- |:--------------------------------- |:------------------------- |:------------------- |
| [`UniqueElements`](@ref)                | Count of unique elements          | `Any`                     | ✔                   |
| [`ValueBinning`](@ref)                  | Binning (histogram)               | `Vector`, `StateSpaceSet` | ✔                   |
| [`OrdinalPatterns`](@ref)               | Ordinal patterns                  | `Vector`, `StateSpaceSet` | ✔                   |
| [`SpatialOrdinalPatterns`](@ref)        | Ordinal patterns in space         | `Array`                   | ✔                   |
| [`Dispersion`](@ref)                    | Dispersion patterns               | `Vector`                  | ✔                   |
| [`SpatialDispersion`](@ref)             | Dispersion patterns in space      | `Array`                   | ✔                   |
| [`CosineSimilarityBinning`](@ref)       | Cosine similarity                 | `Vector`                  | ✔                   |
| [`BubbleSortSwaps`](@ref)               | Swap counts when sorting          | `Vector`                  | ✔                   |
| [`SequentialPairDistances`](@ref)       | Sequential state vector distances | `Vector`, `StateSpaceSet` | ✔                   |
| [`TransferOperator`](@ref)              | Binning (transfer operator)       | `Vector`, `StateSpaceSet` | ✖                   |
| [`NaiveKernel`](@ref)                   | Kernel density estimation         | `StateSpaceSet`           | ✖                   |
| [`WeightedOrdinalPatterns`](@ref)       | Ordinal patterns                  | `Vector`, `StateSpaceSet` | ✖                   |
| [`AmplitudeAwareOrdinalPatterns`](@ref) | Ordinal patterns                  | `Vector`, `StateSpaceSet` | ✖                   |
| [`WaveletOverlap`](@ref)                | Wavelet transform                 | `Vector`                  | ✖                   |
| [`PowerSpectrum`](@ref)                 | Fourier transform                 | `Vector`                  | ✖                   |

In the column "input data" it is assumed that the `eltype` of the input is `<: Real`.

## Usage

Outcome spaces are used as input to

  * [`probabilities`](@ref)/[`allprobabilities_and_outcomes`](@ref) for computing   probability mass functions.
  * [`outcome_space`](@ref), which returns the elements of the outcome space.
  * [`total_outcomes`](@ref), which returns the cardinality of the outcome space.
  * [`counts`](@ref)/[`counts_and_outcomes`](@ref)/[`allcounts_and_outcomes`](@ref), for    obtaining raw counts instead of probabilities (only for counting-compatible outcome   spaces).

## Counting-compatible vs. non-counting compatible outcome spaces

There are two main types of outcome spaces.

  * Counting-compatible outcome spaces have a well-defined   way of counting how often each point in the (encoded) input data is mapped to a   particular outcome $\omega_i$. These outcome spaces use   [`encode`](@ref) to discretize the input data. Examples are   [`OrdinalPatterns`](@ref) (which encodes input data into ordinal patterns) or   [`ValueBinning`](@ref) (which discretizes points onto a regular grid).   The table below lists which outcome spaces are counting compatible.
  * Non-counting compatible outcome spaces have no well-defined way of counting explicitly   how often each point in the input data is mapped to a particular outcome $\omega_i$.   Instead, these outcome spaces returns a vector of pre-normalized "relative counts", one   for each outcome $\omega_i$. Examples are [`WaveletOverlap`](@ref) or   [`PowerSpectrum`](@ref).

Counting-compatible outcome spaces can be used with *any* [`ProbabilitiesEstimator`](@ref) to convert counts into probability mass functions. Non-counting-compatible outcome spaces can only be used with the maximum likelihood ([`RelativeAmount`](@ref)) probabilities estimator, which estimates probabilities precisely by the relative frequency of each outcome (formally speaking, the [`RelativeAmount`](@ref) estimator also requires counts, but for the sake of code consistency, we allow it to be used with relative frequencies as well).

The function [`is_counting_based`](@ref) can be used to check whether an outcome space is based on counting.

## Deducing the outcome space (from data)

Some outcome space models can deduce $\Omega$ without knowledge of the input, such as [`OrdinalPatterns`](@ref). Other outcome spaces require knowledge of the input data for concretely specifying $\Omega$, such as [`ValueBinning`](@ref) with [`RectangularBinning`](@ref). If `o` is some outcome space model and `x` some input data, then [`outcome_space`](@ref)`(o, x)` returns the possible outcomes $\Omega$. To get the cardinality of $\Omega$, use [`total_outcomes`](@ref).

## Implementation details

The element type of $\Omega$ varies between outcome space models, but it is guaranteed to be *hashable* and *sortable*. This allows for conveniently tracking the counts of a specific event across experimental realizations, by using the outcome as a dictionary key and the counts as the value for that key (or, alternatively, the key remains the outcome and one has a vector of probabilities, one for each experimental realization).
