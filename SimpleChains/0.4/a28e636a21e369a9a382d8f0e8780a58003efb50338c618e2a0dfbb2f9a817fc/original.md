```
FrontLastPenalty(SimpleChain, frontpen(λ₁...), lastpen(λ₂...))
```

Applies `frontpen` to all but the last layer, applying `lastpen` to the last layer instead. "Last layer" here ignores the loss function, i.e. if the last element of the chain is a loss layer, the then `lastpen` applies to the layer preceding this.
