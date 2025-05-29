```
DecayChainsLS(; k, Xlineshape, jp, Ps, tbs)
```

Generate decay chains with all possible couplings based on the specified parameters.

# Arguments

  * `k`: index of spectator that specifies the decay chain.
  * `Xlineshape`: Lambda function for the lineshape of the resonance.
  * `jp`: Spin-parity quantum numbers of the resonance (e.g., `jp = "1/2-"`).
  * `Ps`: Parity quantum numbers of the three-body system (e.g., `Ps = ThreeBodyParities('+','+','+'; P0='+')`).
  * `tbs`: Three-body-system structure that defines the involved particles and their properties.

# Returns

  * An array of `DecayChain` objects representing all possible couplings for the given decay configuration.

# Notes

The function computes the possible coupling combinations (`ls` x `LS`). For each combination, a `DecayChain` object is created with the appropriate recoupling terms (`Hij`, `HRk`).

# Example

```julia DecayChainsLS(     k=3, Xlineshape=σ->1.0, jp="1/2-", Ps=ThreeBodyParities('+','+','+'; P0='+'),     tbs=ThreeBodySystem(         ThreeBodyMasses(1, 2, 3; m0=7.0),         ThreeBodySpins(1, 2, 0; h0=3)     ) )
