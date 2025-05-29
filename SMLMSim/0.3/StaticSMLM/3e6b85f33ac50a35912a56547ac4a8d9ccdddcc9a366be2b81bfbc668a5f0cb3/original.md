```
StaticSMLMParams <: SMLMSimParams
```

Parameters for static SMLM simulation.

# Fields

  * `density::Float64`: density in particles per square micron
  * `σ_psf::Float64`: PSF width in microns
  * `minphotons::Int`: minimum photons for detection
  * `ndatasets::Int`: number of datasets to simulate
  * `nframes::Int`: number of frames per dataset
  * `framerate::Float64`: frames per second
  * `ndims::Int`: dimensionality (2 or 3)
  * `zrange::Vector{Float64}`: axial range for 3D simulations [min*z, max*z]

# Examples

```julia
# Default parameters
params = StaticSMLMParams()

# Custom parameters
params = StaticSMLMParams(
    density = 2.0,              # 2 particles per μm²
    σ_psf = 0.15,         # 150nm PSF width
    minphotons = 100,     # minimum photons for detection
    ndatasets = 5,        # 5 independent datasets
    nframes = 2000,       # 2000 frames per dataset
    framerate = 100.0,    # 100 frames per second
    ndims = 3,            # 3D simulation
    zrange = [-2.0, 2.0]  # 4μm axial range
)
```
