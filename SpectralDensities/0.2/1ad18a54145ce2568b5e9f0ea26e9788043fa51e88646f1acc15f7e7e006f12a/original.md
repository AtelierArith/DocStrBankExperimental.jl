```
GaussianCutoffSD(J::AbstractSD, ωcutoff)
```

Construct a spectral density with a Gaussian frequency cutoff using the underlying spectral density `J` and the given frequency cutoff `ωcutoff`.

# Arguments

  * `J::AbstractSD`: The underlying spectral density.
  * `ωcutoff`: The frequency cutoff.

# Returns

  * An instance of the `GaussianCutoffSD` struct representing the spectral density with a Gaussian frequency cutoff.
