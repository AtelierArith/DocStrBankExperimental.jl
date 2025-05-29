```
DiffusionSMLMParams <: SMLMSimParams
```

Parameters for diffusion-based SMLM simulation using Smoluchowski dynamics.

# Fields

  * `density::Float64`: number density (molecules/μm²)
  * `box_size::Float64`: simulation box size (μm)
  * `diff_monomer::Float64`: monomer diffusion coefficient (μm²/s)
  * `diff_dimer::Float64`: dimer diffusion coefficient (μm²/s)
  * `diff_dimer_rot::Float64`: dimer rotational diffusion coefficient (rad²/s)
  * `k_off::Float64`: dimer dissociation rate (s⁻¹)
  * `r_react::Float64`: reaction radius (μm)
  * `d_dimer::Float64`: monomer separation in dimer (μm)
  * `dt::Float64`: time step (s)
  * `t_max::Float64`: total simulation time (s)
  * `ndims::Int`: number of dimensions (2 or 3)
  * `boundary::String`: boundary condition type ("periodic" or "reflecting")
  * `camera_framerate::Float64`: camera frames per second (Hz)
  * `camera_exposure::Float64`: camera exposure time per frame (s)

# Examples

```julia
# Default parameters
params = DiffusionSMLMParams()

# Custom parameters
params = DiffusionSMLMParams(
    density = 1.0,           # 1 molecule per μm²
    box_size = 20.0,         # 20μm × 20μm box
    diff_monomer = 0.2,      # 0.2 μm²/s
    diff_dimer = 0.1,        # 0.1 μm²/s
    diff_dimer_rot = 0.8,    # 0.8 rad²/s
    k_off = 0.1,             # 0.1 s⁻¹
    r_react = 0.02,          # 20nm reaction radius
    d_dimer = 0.06,          # 60nm dimer separation
    dt = 0.005,              # 5ms time step
    t_max = 20.0,            # 20s simulation
    ndims = 3,               # 3D simulation
    boundary = "reflecting", # reflecting boundaries
    camera_framerate = 20.0, # 20 frames per second
    camera_exposure = 0.04   # 40ms exposure per frame
)
```
