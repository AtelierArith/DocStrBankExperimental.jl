```
OrthogonalIntervalProbabilities{N, P <: IntervalProbabilities}
```

A tuple of `IntervalProbabilities` for (marginal) transition probabilities from all source/action pairs to the target states along each axis, with target states/marginals on the rows and source states or source/action pairs on the columns. The source states are ordered in  a column-major order, i.e., the first axis of source states is the fastest, similar to the ordering of a multi-dimensional array in Julia.  E.g. for an `OrthogonalIntervalProbabilities` with `source_dims == (3, 3, 3)` and 2 actions for each source state $\{a_1, a_2\}$,  the columns in order represent the collowing:

$$
    ((1, 1, 1), a_1), ((1, 1, 1), a_2), (2, 1, 1), a_1), ((2, 1, 1), a_2), ..., ((3, 3, 3), a_1), ((3, 3, 3), a_2).
$$

The number of target states correspond to the number of rows in the transition probabilities of each axis.

### Fields

  * `probs::NTuple{N, P}`: A tuple of `IntervalProbabilities` for (marginal) transition probabilities along each axis.
  * `source_dims::NTuple{N, Int32}`: The dimensions of the orthogonal probabilities for the source axis. This is flattened to a single dimension for indexing.

### Examples

An example of OrthogonalIntervalProbabilities with 3 axes and 3 states for each axis, only one action per state.  Therefore, the `source_dims` is (3, 3, 3) and the number of columns of the transition probabilities is 27.

```jldoctest
lower1 = [
    1/15 3/10 1/15 3/10 1/30 1/3 7/30 4/15 1/6 1/5 1/10 1/5 0 7/30 7/30 1/5 2/15 1/6 1/10 1/30 1/10 1/15 1/10 1/15 4/15 4/15 1/3
    1/5 4/15 1/10 1/5 3/10 3/10 1/10 1/15 3/10 3/10 7/30 1/5 1/10 1/5 1/5 1/30 1/5 3/10 1/5 1/5 1/10 1/30 4/15 1/10 1/5 1/6 7/30
    4/15 1/30 1/5 1/5 7/30 4/15 2/15 7/30 1/5 1/3 2/15 1/6 1/6 1/3 4/15 3/10 1/30 3/10 3/10 1/10 1/15 1/30 2/15 1/6 1/5 1/10 4/15
]
upper1 = [
    7/15 17/30 13/30 3/5 17/30 17/30 17/30 13/30 3/5 2/3 11/30 7/15 0 1/2 17/30 13/30 7/15 13/30 17/30 13/30 2/5 2/5 2/3 2/5 17/30 2/5 19/30
    8/15 1/2 3/5 7/15 8/15 17/30 2/3 17/30 11/30 7/15 19/30 19/30 13/15 1/2 17/30 13/30 3/5 11/30 8/15 7/15 7/15 13/30 8/15 2/5 8/15 17/30 3/5
    11/30 1/3 2/5 8/15 7/15 3/5 2/3 17/30 2/3 8/15 2/15 3/5 2/3 3/5 17/30 2/3 7/15 8/15 2/5 2/5 11/30 17/30 17/30 1/2 2/5 19/30 13/30
]
prob1 = IntervalProbabilities(; lower = lower1, upper = upper1)

lower2 = [
    1/10 1/15 3/10 0 1/6 1/15 1/15 1/6 1/6 1/30 1/10 1/10 1/3 2/15 3/10 4/15 2/15 2/15 1/6 7/30 1/15 2/15 1/10 1/3 7/30 1/30 7/30
    3/10 1/5 3/10 2/15 0 1/30 0 1/15 1/30 7/30 1/30 1/15 7/30 1/15 1/6 1/30 1/10 1/15 3/10 0 3/10 1/6 3/10 1/5 0 7/30 2/15
    3/10 4/15 1/10 3/10 2/15 1/3 3/10 1/10 1/6 3/10 7/30 1/6 1/15 1/15 1/10 1/5 1/5 4/15 1/15 1/3 2/15 1/15 1/5 1/5 1/15 7/30 1/15
]
upper2 = [
    2/5 17/30 3/5 11/30 3/5 7/15 19/30 2/5 3/5 2/3 2/3 8/15 8/15 19/30 8/15 8/15 13/30 13/30 13/30 17/30 17/30 13/30 11/30 19/30 8/15 2/5 8/15
    1/3 13/30 11/30 2/5 2/3 2/3 0 13/30 1/2 17/30 17/30 1/3 2/5 1/3 13/30 11/30 8/15 1/3 1/2 8/15 8/15 8/15 8/15 2/5 3/5 2/3 13/30
    17/30 3/5 8/15 1/2 7/15 1/2 2/3 17/30 11/30 2/5 1/2 7/15 2/5 17/30 11/30 2/5 11/30 2/3 1/3 2/3 17/30 8/15 17/30 3/5 2/5 19/30 11/30
]
prob2 = IntervalProbabilities(; lower = lower2, upper = upper2)

lower3 = [
    4/15 1/5 3/10 3/10 4/15 7/30 1/5 4/15 7/30 1/6 1/5 0 1/15 1/30 3/10 1/3 2/15 1/15 7/30 4/15 1/10 1/3 1/5 7/30 1/30 1/5 7/30
    2/15 4/15 1/10 1/30 7/30 2/15 1/15 1/30 3/10 1/3 1/5 1/10 2/15 1/30 2/15 4/15 0 4/15 1/5 4/15 1/10 1/10 1/3 7/30 3/10 1/3 3/10
    1/5 1/3 3/10 1/10 1/15 1/10 1/30 1/5 2/15 7/30 1/3 2/15 1/10 1/6 3/10 1/5 7/30 1/30 0 1/30 1/15 2/15 1/6 7/30 4/15 4/15 7/30
]
upper3 = [
    3/5 17/30 1/2 3/5 19/30 2/5 8/15 1/3 11/30 2/5 17/30 13/30 2/5 3/5 3/5 11/30 1/2 11/30 2/3 17/30 3/5 7/15 19/30 1/2 3/5 1/3 19/30
    3/5 2/3 13/30 19/30 1/3 2/5 17/30 7/15 11/30 3/5 19/30 7/15 2/5 8/15 17/30 11/30 19/30 13/30 2/3 17/30 8/15 13/30 13/30 3/5 1/2 8/15 8/15
    3/5 2/3 1/2 1/2 2/3 7/15 3/5 3/5 1/2 1/3 2/5 8/15 2/5 11/30 1/3 8/15 7/15 13/30 0 2/5 11/30 19/30 19/30 2/5 1/2 7/15 7/15
]
prob3 = IntervalProbabilities(; lower = lower3, upper = upper3)

prob = OrthogonalIntervalProbabilities((prob1, prob2, prob3), (Int32(3), Int32(3), Int32(3)))
```
