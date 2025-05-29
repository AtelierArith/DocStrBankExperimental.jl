```
modefreq(model::Bar, fmax, bc = :CC)
modefreq(model::Rod, fmax, bc = :CC)
modefreq(model::Strings, fmax, bc = :CC)
modefreq(model::Beam, fmax, bc = :SS)
```

Computes the natural frequencies of a longitudinal or torsional bar up to fmax

**Inputs**

  * `model`: Structure containing the bar data
  * `fmax`: Maximum frequency for calculating the mode shapes [Hz]
  * `bc`: Boundary conditions

      * For all OneDStructure

          * `:CC`: Clamped - Clamped
          * `:CF`: Clamped - Free
          * `:FF`: Free - Free
      * For beams

          * `:SS`: Simply Supported - Simply Supported
          * `:SC`: Simply Supported - Clamped
          * `:SF`: Simply Supported - Free

**Outputs**

  * `ωn`: Natural frequencies calculated up to ωmax = 2π*fmax [Hz]
  * `kn`: Vector of modal wavenumbers
