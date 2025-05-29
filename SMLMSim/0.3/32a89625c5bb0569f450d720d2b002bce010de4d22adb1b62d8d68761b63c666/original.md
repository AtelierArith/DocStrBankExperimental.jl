```
SMLMSim
```

Main module for the SMLMSim.jl package.

# API Overview

For a comprehensive overview of the API, use the help mode on `api_overview`:

```
?api_overview
```

Or access the complete API documentation programmatically:

```
docs = SMLMSim.api_overview()
```

This package provides tools for simulating Single Molecule Localization Microscopy (SMLM) data. It includes modules for:

  * **Core:** Fundamental types (molecules, patterns) and photophysics simulation (CTMC, blinking).
  * **StaticSMLM:** Simulating static emitters with blinking and localization noise.
  * **InteractionDiffusion:** Simulating diffusing and interacting emitters (e.g., dimerization) using Smoluchowski dynamics.
  * **CameraImages:** Generating simulated camera images from emitter data, including noise models.

The main `SMLMSim` module re-exports key types and functions from these submodules to provide a unified user interface.

# Usage

```julia
using SMLMSim

# Example: Static simulation
params_static = StaticSMLMParams(density=1.0, σ_psf=0.13)
_, _, smld_noisy = simulate(params_static)

# Example: Diffusion simulation
params_diff = DiffusionSMLMParams(density=0.5, diff_monomer=0.1)
smld_diff = simulate(params_diff)

# Example: Generate images
psf = GaussianPSF(0.15)
images = gen_images(smld_noisy, psf)
```
