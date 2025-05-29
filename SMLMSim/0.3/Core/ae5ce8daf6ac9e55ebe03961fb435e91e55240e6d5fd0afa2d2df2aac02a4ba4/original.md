```
kinetic_model(smld::BasicSMLD, f::Molecule, nframes::Int, framerate::Real;
             ndatasets::Int=1, minphotons=50.0, state1::Int=2)
```

Generate kinetic blinking model from existing localization data.

# Arguments

  * `smld::BasicSMLD`: Input SMLD containing true emitter positions
  * `f::Molecule`: Fluorophore model with kinetic rates
  * `nframes::Int`: Number of frames to simulate
  * `framerate::Real`: Frame rate in Hz
  * `ndatasets::Int=1`: Number of independent datasets to generate
  * `minphotons::Float64=50.0`: Minimum photons for detection
  * `state1::Union{Int, Symbol}=:equilibrium`: Initial state specification:

      * `::Int`: Specific state to start in (1=on, 2=off typically)
      * `:equilibrium`: Sample from equilibrium distribution (default)

# Returns

  * `BasicSMLD`: New SMLD with simulated blinking kinetics

# Details

For each unique position in the input SMLD:

1. Simulates fluorophore blinking using the kinetic model
2. Creates emitters for frames where photon count exceeds threshold
3. Preserves track_id for linking emitters from same position
4. Maintains camera and extends metadata from input SMLD

# Example

```julia
camera = IdealCamera(1:128, 1:128, 0.1)
pattern = Nmer2D()
smld_true, _, _ = simulate(pattern=pattern, camera=camera)

# Add blinking kinetics
fluor = GenericFluor(; γ=10000.0, q=[-10.0 10.0; 1e-1 -1e-1])
smld_model = kinetic_model(smld_true, fluor, 1000, 10.0)
```

# Note

The emitter type (2D/3D) is automatically determined from the input SMLD. Position uncertainties are initialized to 0 and can be set using the apply_noise() function.
