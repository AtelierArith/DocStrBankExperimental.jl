```
bellman(V, prob; upper_bound = false)
```

Compute robust Bellman update with the value function `V` and the interval probabilities `prob`  that upper or lower bounds the expectation of the value function `V` via O-maximization [1]. Whether the expectation is maximized or minimized is determined by the `upper_bound` keyword argument. That is, if `upper_bound == true` then an upper bound is computed and if `upper_bound == false` then a lower bound is computed.

### Examples

```jldoctest
prob = IntervalProbabilities(;
    lower = sparse_hcat(
        SparseVector(15, [4, 10], [0.1, 0.2]),
        SparseVector(15, [5, 6, 7], [0.5, 0.3, 0.1]),
    ),
    upper = sparse_hcat(
        SparseVector(15, [1, 4, 10], [0.5, 0.6, 0.7]),
        SparseVector(15, [5, 6, 7], [0.7, 0.5, 0.3]),
    ),
)

Vprev = collect(1:15)
Vcur = bellman(Vprev, prob; upper_bound = false)
```

!!! note
    This function will construct a workspace object and an output vector. For a hot-loop, it is more efficient to use `bellman!` and pass in pre-allocated objects.


[1] M. Lahijanian, S. B. Andersson and C. Belta, "Formal Verification and Synthesis for Discrete-Time Stochastic Systems," in IEEE Transactions on Automatic Control, vol. 60, no. 8, pp. 2031-2045, Aug. 2015, doi: 10.1109/TAC.2015.2398883.
