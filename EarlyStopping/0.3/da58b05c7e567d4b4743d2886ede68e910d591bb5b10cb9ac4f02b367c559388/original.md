```
PQ(; alpha=0.75, k=5, tol=eps(Float64))
```

A stopping criterion for training iterative supervised learners.

A stop is triggered when Prechelt's progress-modified generalization loss exceeds the threshold $PQ_T > alpha$, or if the training progress drops below $P_j ≤ tol$. Here `k` is the number of training (in-sample) losses used to estimate the training progress.

## Context and explanation of terminology

The *training progress* at time $j$ is defined by

$P_j = 1000 |M - m|/|m|$

where $M$ is the mean of the last `k` training losses $F_1, F_2, …, F_k$ and $m$ is the minimum value of those losses.

The *progress-modified generalization loss* at time $t$ is then given by

$PQ_t = GL_t / P_t$

where $GL_t$ is the generalization loss at time $t$; see [`GL`](@ref).

PQ will stop when the following are true:

1. At least `k` training samples have been collected via `done!(c::PQ, loss; training = true)` or `update_training(c::PQ, loss, state)`
2. The last update was an out-of-sample update. (`done!(::PQ, loss; training=true)` is always false)
3. The progress-modified generalization loss exceeds the threshold $PQ_t > alpha$ **OR** the training progress stalls $P_j ≤ tol$.

Reference: [Prechelt, Lutz (1998): "Early Stopping- But When?", in *Neural Networks: Tricks of the Trade*, ed. G. Orr, Springer.](https://link.springer.com/chapter/10.1007%2F3-540-49430-8_3).
