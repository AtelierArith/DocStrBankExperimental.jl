```
hardware_transform(h::BloqadeExpr.RydbergHamiltonian;device_capabilities::DeviceCapabilities=get_device_capabilities())
```

Given the constraints of the hardware via `device_capabilities`, transforms `h` into one the machine is capable of executing as well as:

  * The mean squared error between original positions of the atoms and the transformed ones
  * The 1-norm of the difference between the original and transformed waveforms

which are all stored in a [`HardwareTransformInfo`](@ref) struct.

`hardware_transform` expects that ALL waveforms `h` can have specified (Ω, Δ, ϕ) are explicitly defined. If there is a waveform that is not being used, a [`BloqadeWaveforms.constant`](@ref) waveform should be created with value zero to indicate non-use.

Note that not all atom position constraints are accounted for, such as the maximum lattice width, lattice height,  and minimum supported spacings. Only position resolution is automatically accounted for. This may result in the [`validation`](@ref) function failing and requiring user intervention to modify the atom  positions such that they satisfy the other constraints.

# Logs/Warnings/Exceptions

Debug logs are *always* emitted containing the error (defined as the 1-norm of the difference between the original waveform and the transformed waveform) across all waveforms (Ω, Δ, ϕ) as well as the  Mean Squared Error between the original atom positions and the adjusted atom positions.

The debug logs/warnings from constituent functions [`hardware_transform_Ω`](@ref), [`hardware_transform_Δ`](@ref), [`hardware_transform_ϕ`](@ref) are also emitted should the  waveforms in `h` cause them to.

See also [`hardware_transform_atoms`](@ref), [`hardware_transform_Ω`](@ref), [`hardware_transform_Δ`](@ref), [`hardware_transform_ϕ`](@ref).

# Examples

```jldoctest; setup:=(using BloqadeExpr, BloqadeLattices)
julia> atom_positions = AtomList([(1.12,), (2.01,), (3.01,)]);

julia> Δ = Ω = ϕ = sinusoidal(duration=2, amplitude=1.3*π);

julia> h = rydberg_h(atom_positions; Ω=Ω,Δ=Δ,ϕ=ϕ)
nqubits: 3
+
├─ [+] ∑ 2π ⋅ 8.627e5.0/|x_i-x_j|^6 n_i n_j
├─ [+] Ω(t) ⋅∑ e^{ϕ(t) ⋅ im} |0⟩⟨1| + e^{-ϕ(t) ⋅ im} |1⟩⟨0|
└─ [-] Δ(t) ⋅ ∑ n_i


julia> hardware_transform(h)
(nqubits: 3
+
├─ [+] ∑ 2π ⋅ 8.627e5.0/|x_i-x_j|^6 n_i n_j
├─ [+] Ω(t) ⋅∑ e^{ϕ(t) ⋅ im} |0⟩⟨1| + e^{-ϕ(t) ⋅ im} |1⟩⟨0|
└─ [-] Δ(t) ⋅ ∑ n_i
, BloqadeSchema.HardwareTransformInfo(0.5386117854062276, 2.632451578170084, 0.06492452289703464, (Δ = Waveform(_, 2), δ = nothing, Δi = 1.0), 0.013333333333333197))
```
