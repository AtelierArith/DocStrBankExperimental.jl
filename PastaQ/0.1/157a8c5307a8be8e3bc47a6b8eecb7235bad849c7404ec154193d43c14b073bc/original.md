```
runcircuit(
  M::Union{MPS, MPO, ITensor},
  circuit::Vector{<:Vector{<:ITensor}};
  (observer!)=nothing,
  move_sites_back_before_measurements::Bool=false,
  noise = nothing,
  outputlevel = 1,
  outputpath = nothing,
  savestate = false,
  print_metrics = [],
  kwargs...)
```

Apply a quantum circuit to an input state `M`, where the circuit is built out of a sequence of layers of quantum gates. The input state may be an MPS wavefunction $|\psi\rangle$, an MPO density operator $ρ$ (or unitary operator $U$), etc.

By feeding a "layered" circuit, we can enable measurement and keep track of metrics as a function of the circuit's depth.

Other than the keyword arguments of the high-level interface, here we can provide:

  * `(observer!)`: observer object (from Observers.jl).
  * `outputlevel = 1`: amount of printing during calculation.
  * `outputpath = nothing`: if set, save observer on file.
  * `savestate = false`: if `true`, save the `MPS/MPO` on file.
  * `print_metrics = []`: the metrics in the `observed` to print at each depth.`
