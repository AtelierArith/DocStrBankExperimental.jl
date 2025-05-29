```
MultiPhaseCompositionalSystemLV(equation_of_state)
MultiPhaseCompositionalSystemLV(equation_of_state, phases = (LiquidPhase(), VaporPhase()); reference_densities = ones(length(phases)), other_name = "Water")
```

Set up a compositional system for a given `equation_of_state` from `MultiComponentFlash` with two or three phases. If three phases are provided, the phase that is not a liquid or a vapor phase will be treated as immiscible in subsequent simulations and given the name from `other_name` when listed as a component.
