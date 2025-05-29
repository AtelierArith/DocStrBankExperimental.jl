```
AbstractState_specify_phase(handle::Clong, phase::AbstractString)
```

Specify the phase to be used for all further calculations.

# Arguments

  * `handle`: The integer handle for the state class stored in memory
  * `phase`: The string with the phase to use. Possible candidates are listed below:

| Phase name                 |      Condition |
|:-------------------------- | --------------:|
| phase_liquid               |                |
| phase_gas                  |                |
| phase_twophase             |                |
| phase_supercritical        |                |
| phase*supercritical*gas    | p < pc, T > Tc |
| phase*supercritical*liquid | p > pc, T < Tc |
| phase*critical*point       | p = pc, T = Tc |
| phase_unknown              |                |
| phase*not*imposed          |                |

# Example

```julia
julia> heos = AbstractState_factory("HEOS", "Water");
# Do a flash call that is a very low density state point, definitely vapor
julia> @time AbstractState_update(heos, "DmolarT_INPUTS", 1e-6, 300);
  0.025233 seconds (5.23 k allocations: 142.283 KB)
# Specify the phase - for some inputs (especially density-temperature), this will result in a
# more direct evaluation of the equation of state without checking the saturation boundary
julia> AbstractState_specify_phase(heos, "phase_gas");
# We try it again - a bit faster
julia> @time AbstractState_update(heos, "DmolarT_INPUTS", 1e-6, 300);
  0.000050 seconds (5 allocations: 156 bytes)
julia> AbstractState_free(heos);
```
