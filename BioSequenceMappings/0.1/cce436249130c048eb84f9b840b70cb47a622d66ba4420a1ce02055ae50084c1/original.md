```
compute_weights(X::AbstractAlignment, θ = 0.2; normalize = true)
```

Compute phylogenetic correction weights for sequences of `X`.     The weight sequence `S` is `1/N`, where `N` is the number of sequences in `X` at     hamming distance less than `H` from `S` (including `S` itself).     The threshold `H` is `floor(θ⋅L)` where `L` is the sequence length.

The return value is a tuple `(weights, Meff)`, where `Meff` is the sum of weights (pre-normalization). If `normalize`, weights are normalized to sum to one. .
