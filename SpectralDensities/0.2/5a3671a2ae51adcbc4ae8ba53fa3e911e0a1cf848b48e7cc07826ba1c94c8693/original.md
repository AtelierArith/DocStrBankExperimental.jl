```
HardCutoffSD(J::AbstractSD, ωcutoff)
```

Construct a spectral density with a hard frequency cutoff using the underlying spectral density `J` and the given frequency cutoff `ωcutoff`.

# Arguments

  * `J::AbstractSD`: The underlying spectral density.
  * `ωcutoff::Float64`: The frequency cutoff.

# Returns

  * An instance of the `HardCutoffSD` struct representing the spectral density with a hard frequency cutoff.
