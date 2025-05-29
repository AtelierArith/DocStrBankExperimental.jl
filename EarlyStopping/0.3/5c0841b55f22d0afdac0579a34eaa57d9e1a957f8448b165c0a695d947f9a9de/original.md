```
GL(; alpha=2.0)
```

An early stopping criterion for loss-reporting iterative algorithms. 

A stop is triggered when the (rescaled) generalization loss exceeds the threshold `alpha`.

**Terminology.** Suppose $E_1, E_2, ..., E_t$ are a sequence of losses, for example, out-of-sample estimates of the loss associated with some iterative machine learning algorithm. Then the *generalization loss* at time `t`, is given by

$GL_t = 100 (E_t - E_{opt}) \over |E_{opt}|$

where $E_{opt}$ is the minimum value of the sequence.

Reference: [Prechelt, Lutz (1998): "Early Stopping- But When?", in *Neural Networks: Tricks of the Trade*, ed. G. Orr, Springer.](https://link.springer.com/chapter/10.1007%2F3-540-49430-8_3).
