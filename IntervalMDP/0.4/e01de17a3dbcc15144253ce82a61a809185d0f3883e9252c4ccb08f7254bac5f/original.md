```
MixtureIntervalProbabilities{N, P <: OrthogonalIntervalProbabilities, Q <: IntervalProbabilities}
```

A tuple of `OrthogonalIntervalProbabilities` for independent transition probabilities in a mixture that all share the same source/action pairs, and target states. See [OrthogonalIntervalProbabilities](@ref) for more information on the structure of the transition probabilities for each model in the mixture. The mixture is weighted by an `IntervalProbabilities` ambiguity set, called `weighting_probs`.

### Fields

  * `mixture_probs::NTuple{N, P}`: A tuple of `OrthogonalIntervalProbabilities` transition probabilities along each axis.
  * `weighting_probs::Q`: The weighting ambiguity set for the mixture.

### Examples

Below is a simple example of a mixture of two `OrthogonalIntervalProbabilities` with one dimension and the same source/action pairs and target states, and a weighting ambiguity set.

```jldoctest
prob1 = OrthogonalIntervalProbabilities(
    (
        IntervalProbabilities(;
            lower = [
                0.0 0.5
                0.1 0.3
                0.2 0.1
            ],
            upper = [
                0.5 0.7
                0.6 0.5
                0.7 0.3
            ],
        ),
    ),
    (Int32(2),),
)
prob2 = OrthogonalIntervalProbabilities(
    (
        IntervalProbabilities(;
            lower = [
                0.1 0.4
                0.2 0.2
                0.3 0.0
            ],
            upper = [
                0.4 0.6
                0.5 0.4
                0.6 0.2
            ],
        ),
    ),
    (Int32(2),),
)
weighting_probs = IntervalProbabilities(; lower = [
    0.3 0.5
    0.4 0.3
], upper = [
    0.8 0.7
    0.7 0.5
])
mixture_prob = MixtureIntervalProbabilities((prob1, prob2), weighting_probs)
```
