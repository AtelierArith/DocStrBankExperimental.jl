```
RydbergChainSystem(;
    N::Int=3, # number of atoms
    C::Float64=862690*2π,
    distance::Float64=10.0, # μm
    cutoff_order::Int=2, # 1 is nearest neighbor, 2 is next-nearest neighbor, etc.
    local_detune::Bool=false, # If true, include one local detuning pattern.
    all2all::Bool=true, # If true, include all-to-all interactions.
    ignore_Y_drive::Bool=false, # If true, ignore the Y drive. (In the experiments, X&Y drives are implemented by Rabi amplitude and its phase.)
) -> QuantumSystem
```

Returns a `QuantumSystem` object for the Rydberg atom chain in the spin basis     |g⟩ = |0⟩ = [1, 0], |r⟩ = |1⟩ = [0, 1].

$$
H = \sum_i 0.5*\Omega_i(t)\cos(\phi_i(t)) \sigma_i^x - 0.5*\Omega_i(t)\sin(\phi_i(t)) \sigma_i^y - \sum_i \Delta_i(t)n_i + \sum_{i<j} \frac{C}{|i-j|^6} n_i n_j
$$

# Keyword Arguments

  * `N`: Number of atoms.
  * `C`: The Rydberg interaction strength in MHz*μm^6.
  * `distance`: The distance between atoms in μm.
  * `cutoff_order`: Interaction range cutoff, 1 is nearest neighbor, 2 is next nearest neighbor.
  * `local_detune`: If true, include one local detuning pattern.
  * `all2all`: If true, include all-to-all interactions.
  * `ignore_Y_drive`: If true, ignore the Y drive. (In the experiments, X&Y drives are implemented by Rabi amplitude and its phase.)
