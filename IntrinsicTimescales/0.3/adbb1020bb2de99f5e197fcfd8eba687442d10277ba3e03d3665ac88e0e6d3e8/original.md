```
IntrinsicTimescales
```

A Julia package for estimation of timescales from time series data.

# Features

  * Standard techniques for INT calculation: ACW-50, ACW-0, FOOOF
  * Approximate Bayesian Computation (ABC) for parameter inference
  * ADVI for variational inference
  * Multiple model types:

      * Single timescale
      * Single timescale with oscillations
      * Models supporting missing data
  * Summary statistics using periodogram, Welch (from DSP.jl) and Lomb-Scargle (from LombScargle.jl):

      * Autocorrelation function (ACF)
      * Power spectral density (PSD)

# Submodules

  * `Models`: Abstract model types and interfaces
  * `ABC`: Approximate Bayesian Computation algorithms
  * `TuringBackend`: Turing.jl integration for ADVI
  * `SummaryStats`: ACF and PSD implementations
  * `Distances`: Distance metrics for ABC
  * `Utils`: Utility functions for analysis
  * `OrnsteinUhlenbeck`: OU process generation using DifferentialEquations.jl
  * `OneTimescale`: Single timescale model
  * `OneTimescaleAndOsc`: Single timescale with oscillations
  * `OneTimescaleWithMissing`: Single timescale with missing data
  * `OneTimescaleAndOscWithMissing`: Single timescale and oscillations with missing data
  * `Plotting`: Plotting functions for results
