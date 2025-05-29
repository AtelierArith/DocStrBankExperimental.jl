```
AdamOptimizerWithDecay(n_epochs, η₁=1f-2, η₂=1f-6, ρ₁=9f-1, ρ₂=9.9f-1, δ=1f-8)
```

Make an instance of the Adam Optimizer with weight decay.

All except the first argument (the number of epochs) have defaults.

The difference to the standard [`AdamOptimizer`](@ref) is that we change the learning reate $\eta$ in each step. Apart from the *time dependency* of $\eta$ the two algorithms are however equivalent. $\eta(0)$ starts with a high value $\eta_1$ and then exponentially decrease until it reaches $\eta_2$ with

$$
 \eta(t) = \gamma^t\eta_1,
$$

where $\gamma = \exp(\log(\eta_1 / \eta_2) / \mathtt{n\_epochs}).$
