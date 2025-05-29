```
IntervalProbabilities{R, VR <: AbstractVector{R}, MR <: AbstractMatrix{R}}
```

A matrix pair to represent the lower and upper bound transition probabilities from all source states or source/action pairs to all target states. The matrices can be `Matrix{R}` or `SparseMatrixCSC{R}`, or their CUDA equivalents. For memory efficiency, it is recommended to use sparse matrices.

The columns represent the source and the rows represent the target, as if the probability matrix was a linear transformation. Mathematically, let $P$ be the probability matrix. Then $P_{ij}$ represents the probability of transitioning from state $j$ (or with state/action pair $j$) to state $i$. Due to the column-major format of Julia, this is also a more efficient representation (in terms of cache locality).

The lower bound is explicitly stored, while the upper bound is computed from the lower bound and the gap. This choice is  because it simplifies repeated probability assignment using O-maximization [1].

### Fields

  * `lower::MR`: The lower bound transition probabilities from a source state or source/action pair to a target state.
  * `gap::MR`: The gap between upper and lower bound transition probabilities from a source state or source/action pair to a target state.
  * `sum_lower::VR`: The sum of lower bound transition probabilities from a source state or source/action pair to all target states.

### Examples

```jldoctest
dense_prob = IntervalProbabilities(;
    lower = [0.0 0.5; 0.1 0.3; 0.2 0.1],
    upper = [0.5 0.7; 0.6 0.5; 0.7 0.3],
)

sparse_prob = IntervalProbabilities(;
    lower = sparse_hcat(
        SparseVector(15, [4, 10], [0.1, 0.2]),
        SparseVector(15, [5, 6, 7], [0.5, 0.3, 0.1]),
    ),
    upper = sparse_hcat(
        SparseVector(15, [1, 4, 10], [0.5, 0.6, 0.7]),
        SparseVector(15, [5, 6, 7], [0.7, 0.5, 0.3]),
    ),
)
```

[1] M. Lahijanian, S. B. Andersson and C. Belta, "Formal Verification and Synthesis for Discrete-Time Stochastic Systems," in IEEE Transactions on Automatic Control, vol. 60, no. 8, pp. 2031-2045, Aug. 2015, doi: 10.1109/TAC.2015.2398883.
