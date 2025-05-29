```
spgr! = SPGRBlochSim(TR, TE, rf, [spoiling], [nTR], [save_transients])
spgr!(spin, [workspace])
```

Simulate a spoiled gradient-recalled echo (SPGR) scan on `spin`, overwriting the spin's magnetization vector. The resultant magnetization is stored in `spin.M`. If `nTR > 0` and `save_transients === true`, then `spgr!(...)` returns a `Vector` with the magnetization vectors at the echo time for each of the `nTR` simulated TRs.

# Arguments

  * `TR::Real`: Repetition time (ms)
  * `TE::Real`: Echo time (ms)
  * `rf`:

      * `::Real`: Excitation flip angle (rad) (assumes an instantaneous RF pulse)
      * `::AbstractRF`: Excitation RF pulse
  * `spoiling::AbstractSpoiling = IdealSpoiling()`: Type of spoiling to apply
  * `nTR::Val = Val(0)`: Number of TRs to simulate; `Val(0)` indicates to simulate a steady-state scan
  * `save_transients::Val = Val(false)`: Whether or not to return the magnetization vectors at the TE for each of the `nTR` simulated TRs; does nothing if `nTR == 0`

`workspace isa SPGRBlochSimWorkspace`.
