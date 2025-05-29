```
lorentzian(f, u)
```

Compute Lorentzian function values.

# Arguments

  * `f::AbstractVector`: Frequency values
  * `u::Vector`: Parameters [amplitude, knee_frequency]

# Returns

  * Vector of Lorentzian values: amp/(1 + (f/knee)²)
