```
ActionNoise(
    action, # group action G ⊂ Diff(M)
    covariance, # function M -> AbstractPDMat
    basis # fixed basis of Alg(G)
)
```

Covariance defined on Lie algebra. The corresponding distribution centred at x₀  is the push forward of the normal distribution on the Lie algebra by the function ξ ↦ \exp(ξ)⋅x₀.
