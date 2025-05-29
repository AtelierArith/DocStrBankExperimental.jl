```
simulate(params::DiffusionSMLMParams; 
         starting_conditions::Union{Nothing, SMLD, Vector{<:AbstractDiffusingEmitter}}=nothing,
         photons::Float64=1000.0, 
         override_count::Union{Nothing, Int}=nothing,
         kwargs...)
```

Run a Smoluchowski diffusion simulation and return a BasicSMLD object with emitters that have both frame number and timestamp information.

# Arguments

  * `params::DiffusionSMLMParams`: Simulation parameters
  * `starting_conditions::Union{Nothing, SMLD, Vector{<:AbstractDiffusingEmitter}}`: Optional starting emitters
  * `photons::Float64=1000.0`: Number of photons per emitter
  * `override_count::Union{Nothing, Int}=nothing`: Optional override for the number of molecules

# Keyword Arguments

  * Any additional parameters are ignored (allows unified interface with other simulate methods)

# Returns

  * `BasicSMLD`: Single SMLD object containing all emitters across all frames

# Example

```julia
# Set up parameters with camera settings
params = DiffusionSMLMParams(
    density = 0.5,           # molecules per μm²
    box_size = 10.0,         # μm
    camera_framerate = 20.0, # 20 fps
    camera_exposure = 0.04   # 40ms exposure
)

# Run basic simulation
smld = simulate(params)

# Run simulation with exactly 2 particles
smld = simulate(params; override_count=2)

# Use previous simulation state as starting conditions for a new simulation
final_frame = maximum([e.frame for e in smld.emitters])
final_state_emitters = filter(e -> e.frame == final_frame, smld.emitters)
smld_continued = simulate(params; starting_conditions=final_state_emitters)
```
