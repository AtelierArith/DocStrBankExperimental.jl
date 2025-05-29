```
FISP2D{T, Ns, U<:AbstractVector, V<:AbstractMatrix} <: EPGSimulator{T,Ns}
```

This struct is used to simulate gradient-spoiled sequence with varying flip angle scheme and adiabatic inversion prepulse using the EPG model. The TR and TE are fixed throughout the sequence. Instantenous RF excitations are assumed. Slice profile correction is done using the partitioned EPG model, where for each flip angle a vector of RF scaling factors are determined prior to the simulation (using, for example, the small tip-angle approximation or Shinnar LeRoux forward model).

Within each TR, a single time steps is used to simulate the RF excitation. Then, in one time step we go from the end of the RF excitation to the echo time (applying T₁ and T₂ decay, T₁ regrowth and B₀ rotation), and again in one time step from the echo time to the start of the next RF excitation.

# Fields

  * `RF_train::U` Vector with flip angle for each TR with abs.(RF*train) the RF flip angles in degrees and   angle.(RF*train) should be the RF phases in degrees.
  * `sliceprofiles::V` # Matrix with RF scaling factors (a.u.) to simulate slice profile effects.   Each column represents the (flip angle dependent) scaling factors for one position along the slice direction.
  * `TR::T`: Repetition time in seconds, assumed constant during the sequence
  * `TE::T`: Echo time in seconds, assumed constant during the sequence
  * `max_state::Val{Ns}`: Maximum number of states to keep track of in EPG simulation
  * `TI::T`: Inversion delay after the inversion prepulse in seconds
