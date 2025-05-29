```
Descent(η = 1f-1)
Descent(; [eta])
```

Classic gradient descent optimiser with learning rate `η`. For each parameter `p` and its gradient `dp`, this runs `p -= η*dp`.

# Parameters

  * Learning rate (`η == eta`): Amount by which gradients are discounted before updating                      the weights.
