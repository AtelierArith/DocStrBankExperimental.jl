```
Muon(opt = AdamW(eta = 0.0003, beta = (0.9,0.95), lambda = 0.01), η = 0.02, μ = 0.95, λ = 0.01, fallback = Returns(false))
Muon(; [opt, eta, mu, lambda, fallback])
```

Muon - MomentUm Orthogonalized by Newton-schulz (https://github.com/KellerJordan/Muon)

Muon internally runs standard SGD-momentum, and then performs an orthogonalization post-processing step, in which each 2D parameter's update is replaced with the nearest orthogonal matrix using Newton-Schulz iteration.

# Parameters

  * Fallback optimizer (`opt`): Optimizer to use for 1D parameters or when the `fallback` function returns true
  * Learning rate (`η == eta`): Amount by which gradients are discounted before updating the weights
  * Momentum (`μ == mu`): Controls the acceleration of gradient descent in the prominent direction
  * Weight decay (`λ == lambda`): Controls the strength of $L_2$ regularisation.
  * Fallback function (`fallback`): Function to control when, in addition to 1D arrays, the fallback optimizer should be used. Will be passed the parameter array and must return a boolean.

Note: Works best with large batch sizes and may not be suitable for fine-tuning. In nanoGPT speedrun experiments, Muon is used for the internal layer >2D weights, and AdamW is used for the 1D weights, embeddings, and heads.

`Optimisers.adjust!(optimiser_state, η::Real)` will adjust the fallback optimizer's `eta` to `η * (opt.eta / eta)`, and Muon's `eta` to `η`, preserving their ratio, but `Optimisers.adjust!(optimiser, eta = η)` will only adjust Muon's learning rate (allowing you to adjust the fallback optimizer's learning rate separately).
