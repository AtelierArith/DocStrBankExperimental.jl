```
sdoverω(J::T, ω) where T <: AbstractSD
```

Evaluate the spectral density represented by `J` divided by a given frequency `ω`, i.e. `J(ω)/ω`.

# Arguments

  * `J::T`: The spectral density.
  * `ω`: The frequency at which the spectral density is evaluated.

# Returns

  * The spectral density `J(ω)` divided by `ω`.
