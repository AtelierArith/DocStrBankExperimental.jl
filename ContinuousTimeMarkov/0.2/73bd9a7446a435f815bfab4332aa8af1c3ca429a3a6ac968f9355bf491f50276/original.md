```julia
TransitionRateMatrix(Q)

```

Create a transition rate matrix from the argument. This makes a copy, checks that off-diagonal elements are nonnegative, and sets the diagonal so that rows sum to `0`, striving to preserve sparsity and structure.
