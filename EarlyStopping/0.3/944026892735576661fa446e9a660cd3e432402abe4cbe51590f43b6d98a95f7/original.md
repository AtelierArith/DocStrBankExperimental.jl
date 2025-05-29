```
Patience(; n=5)
```

An early stopping criterion for loss-reporting iterative algorithms. 

A stop is triggered by `n` consecutive increases in the loss.

Denoted "*UP*s" in [Prechelt, Lutz (1998): "Early Stopping- But When?", in *Neural Networks: Tricks of the Trade*, ed. G. Orr, Springer.](https://link.springer.com/chapter/10.1007%2F3-540-49430-8_3).

For a customizable loss-based stopping criterion, use [`WithLossDo`](@ref) or [`WithTrainingLossesDo`](@ref) with the `stop_if_true=true` option. 
