```
mese! = MESEBlochSim(TR, TE, nechoes, [rfex, rfref, rephaser, crusher, spoiling])
mese!(spin, [workspace])
```

Simulate a multi-echo spin echo (MESE) scan on `spin`, overwriting the spin's magnetization vector. Returns a `Vector` with the magnetization vectors at each echo.

# Arguments

  * `TR::Real`: Repetition time (ms)
  * `TE::Real`: First echo time, and echo spacing (ms); the first echo time is measured from the middle of the excitation pulse
  * `nechoes::Integer`: Number of echoes to readout
  * `rfex::AbstractRF = InstantaneousRF(π/2)`: Excitation RF pulse
  * `rfref::AbstractRF = InstantaneousRF(π, -π/2)`: Refocussing RF pulse
  * `rephaser::Union{<:GradientSpoiling,Nothing} = nothing`: Slice-select excitation rephasing gradient
  * `crusher::Union{<:GradientSpoiling,Nothing} = nothing`: Crusher gradient (placed on either side of each refocussing pulse)
  * `spoiling::Union{IdealSpoiling,<:GradientSpoiling,Nothing} = IdealSpoiling()`: Type of spoiling to apply

`workspace isa MESEBlochSimWorkspace`.
