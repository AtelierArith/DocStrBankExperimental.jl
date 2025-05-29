```
simulate(params::StaticSMLMParams; 
         starting_conditions::Union{Nothing, SMLD, Vector{<:AbstractEmitter}}=nothing,
         pattern::Pattern=nothing,
         molecule::Molecule=GenericFluor(photons=1e4, k_off=50.0, k_on=1e-2),
         camera::AbstractCamera=IdealCamera(1:128, 1:128, 0.1))
```

Generate simulated static SMLM data with realistic blinking kinetics and localization uncertainty.

# Arguments

  * `params::StaticSMLMParams`: Simulation parameters
  * `starting_conditions::Union{Nothing, SMLD, Vector{<:AbstractEmitter}}`: Optional starting conditions instead of generating patterns
  * `pattern::Pattern`: Pattern to use (default depends on params.ndims)
  * `molecule::Molecule`: Fluorophore model for blinking simulation
  * `camera::AbstractCamera`: Camera model for detection simulation

# Returns

  * `Tuple{BasicSMLD, BasicSMLD, BasicSMLD}`: (true*positions, model*kinetics, noisy_data)

      * true_positions: Ground truth emitter positions
      * model_kinetics: Positions with simulated blinking
      * noisy_data: Positions with blinking and localization uncertainty

# Example

```julia
# Create parameters
params = StaticSMLMParams(
    density = 2.0,              # 2 patterns per μm²
    σ_psf = 0.15,         # 150nm PSF width
    minphotons = 100,     # 100 photons for detection
    ndatasets = 5,        # 5 independent datasets
    nframes = 2000,       # 2000 frames
    framerate = 100.0     # 100 frames per second
)

# Run simulation with Nmer pattern
pattern = Nmer3D(n=6, d=0.2)
smld_true, smld_model, smld_noisy = simulate(params; pattern=pattern)

# Run with custom starting conditions
custom_emitters = [
    Emitter2DFit{Float64}(x, y, 1.0, 0.0, 0.0, 0.0, 0.0, 0.0; track_id=i)
    for (i, (x, y)) in enumerate(zip(rand(10), rand(10)))
]
smld_true, smld_model, smld_noisy = simulate(params; starting_conditions=custom_emitters)
```

# Note

  * The `params.σ_psf` value is used directly for lateral uncertainty (σx, σy) in both 2D and 3D.
  * For 3D simulations, the axial uncertainty (σz) is scaled by a factor of 3 (i.e., σz = 3 * σ_psf).
  * If `starting_conditions` is provided, it will be used instead of generating patterns.
