```
mutable struct ST8C <: AVR
    OEL_Flag::Int
    UEL_Flag::Int
    SCL_Flag::Int
    SW1_Flag::Int
    Tr::Float64
    K_pr::Float64
    K_ir::Float64
    Vpi_lim::MinMax
    K_pa::Float64
    K_ia::Float64
    Va_lim::MinMax
    K_a::Float64
    T_a::Float64
    Vr_lim::MinMax
    K_f::Float64
    T_f::Float64
    K_c1::Float64
    K_p::Float64
    K_i1::Float64
    X_l::Float64
    θ_p::Float64
    VB1_max::Float64
    K_c2::Float64
    K_i2::Float64
    VB2_max::Float64
    V_ref::Float64
    Ifd_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    states_types::Vector{StateTypes}
    internal::InfrastructureSystemsInternal
end
```

In these excitation systems, voltage (and also current in compounded systems) is transformed to an appropriate level. Rectifiers, either controlled or non-controlled, provide the necessary direct current for the generator field. Parameters of IEEE Std 421.5 Type ST8C Excitacion System. ST8C in PSSE and PSLF

# Arguments

  * `OEL_Flag::Int`: OEL Flag for ST8C: <2: Summation at Voltage Error, 2: OEL takeover at gate, validation range: `(0, 2)`
  * `UEL_Flag::Int`: UEL Flag for ST8C: <2: Summation at Voltage Error, 2: UEL takeover at gate, validation range: `(0, 2)`
  * `SCL_Flag::Int`: SCL Flag for ST8C: <2: Summation at Voltage Error, 2: SCL Takeover at UEL and OEL gates, validation range: `(0, 2)`
  * `SW1_Flag::Int`: SW1 Flag for Power Source Selector for ST8C: <2: Source from generator terminal voltage, 2: Independent power source, validation range: `(0, 2)`
  * `Tr::Float64`: Regulator input filter time constant in seconds, validation range: `(0, nothing)`
  * `K_pr::Float64`: Regulator proportional gain (pu), validation range: `(0, nothing)`
  * `K_ir::Float64`: Regulator integral gain (pu), validation range: `(0, nothing)`
  * `Vpi_lim::MinMax`: Regulator input limits (Vpi*min, Vpi*max)
  * `K_pa::Float64`: Field current regulator proportional gain (pu), validation range: `(0, nothing)`
  * `K_ia::Float64`: Field current regulator integral gain (pu), validation range: `(0, nothing)`
  * `Va_lim::MinMax`: Field current regulator output limits (Va*min, Va*max)
  * `K_a::Float64`: Field current regulator proportional gain (pu), validation range: `(0, nothing)`
  * `T_a::Float64`: Controlled rectifier bridge equivalent time constant in seconds, validation range: `(0, nothing)`
  * `Vr_lim::MinMax`: Voltage regulator limits (Vr*min, Vr*max)
  * `K_f::Float64`: Exciter field current feedback gain (pu), validation range: `(0, nothing)`
  * `T_f::Float64`: Field current feedback time constant in seconds, validation range: `(0, nothing)`
  * `K_c1::Float64`: Rectifier loading factor proportional to commutating reactance (pu), validation range: `(0, nothing)`
  * `K_p::Float64`: Potential circuit (voltage) gain coefficient (pu), validation range: `(0, nothing)`
  * `K_i1::Float64`: Potential circuit (current) gain coefficient (pu), validation range: `(0, nothing)`
  * `X_l::Float64`: Reactance associated with potential source (pu), validation range: `(0, nothing)`
  * `θ_p::Float64`: Potential circuit phase angle (degrees), validation range: `(0, nothing)`
  * `VB1_max::Float64`: Maximum available exciter voltage (pu), validation range: `(0, nothing)`
  * `K_c2::Float64`: Rectifier loading factor proportional to commutating reactance (pu), validation range: `(0, nothing)`
  * `K_i2::Float64`: Potential circuit (current) gain coefficient (pu), validation range: `(0, nothing)`
  * `VB2_max::Float64`: Maximum available exciter voltage (pu), validation range: `(0, nothing)`
  * `V_ref::Float64`: (default: `1.0`) Reference Voltage Set-point (pu), validation range: `(0, nothing)`
  * `Ifd_ref::Float64`: (default: `1.0`) Reference Field Current Set-point (pu), validation range: `(0, nothing)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `states::Vector{Symbol}`: (**Do not modify.**) The [states](@ref S) are:

```
Vm: Sensed terminal voltage,
x_a1: Regulator Integrator state,
x_a2: Field Current regulator state,
x_a3: Controller rectifier bridge state,
x_a4: Regulator Feedback state
```

  * `n_states::Int`: (**Do not modify.**) ST8C has 5 states
  * `states_types::Vector{StateTypes}`: (**Do not modify.**) ST8C has 5 states
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
