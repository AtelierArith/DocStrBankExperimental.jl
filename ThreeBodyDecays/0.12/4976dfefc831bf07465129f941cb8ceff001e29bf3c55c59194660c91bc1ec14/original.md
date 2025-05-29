```
DecayChainLS(; k, Xlineshape, jp, Ps, tbs)
```

Constructs a decay chain with the smallest spin-orbit coupling.

# Arguments

  * `k`: Index of the spectator particle.
  * `Xlineshape`: Lambda function for the lineshape of the resonance.
  * `jp`: Spin-parity of the resonance (e.g., `jp = "1/2-"`).
  * `Ps`: Parities of the three-body system (e.g., `Ps = ThreeBodyParities('+','+','+'; P0='+')`).
  * `tbs`: Three-body system structure.

# Example

```julia DecayChainLS(     k = 1,     Xlineshape = x -> 1 / (x - 1im),     jp = "1/2-",     Ps = ThreeBodyParities('+', '+', '+'; P0 = '+'),     tbs = ThreeBodySystem(1.0, 2.0, 3.0; m0 = 4.0) )
