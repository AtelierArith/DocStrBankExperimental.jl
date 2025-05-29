```
raw = signal_to_raw_data(signal, seq; phantom_name, sys, sim_params)
```

Transforms the raw signal into a RawAcquisitionData struct (nearly equivalent to the ISMRMRD format) used for reconstruction with MRIReco.

# Arguments

  * `signal`: (`::Matrix{Complex}`) raw signal matrix
  * `seq`: (`::Sequence`) Sequence struct

# Keywords

  * `phantom_name`: (`::String`, `="Phantom"`) phantom name
  * `sys`: (`::Scanner`, `=Scanner()`) Scanner struct
  * `sim_params`: (`::Dict{String, Any}`, `=Dict{String,Any}()`) simulation parameter dictionary

# Returns

  * `raw`: (`::RawAcquisitionData`) RawAcquisitionData struct

# Examples

```julia-repl
julia> seq_file = joinpath(dirname(pathof(KomaMRI)), "../examples/1.sequences/epi_se.seq")

julia> sys, obj, seq = Scanner(), brain_phantom2D(), read_seq(seq_file)

julia> sim_params = KomaMRICore.default_sim_params(); sim_params["return_type"] = "mat"

julia> signal = simulate(obj, seq, sys; sim_params)

julia> raw = signal_to_raw_data(signal, seq)

julia> plot_signal(raw)
```
