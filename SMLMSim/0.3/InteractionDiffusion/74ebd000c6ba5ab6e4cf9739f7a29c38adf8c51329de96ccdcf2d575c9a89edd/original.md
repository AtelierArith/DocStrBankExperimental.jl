```
analyze_dimer_fraction(smld::BasicSMLD)
```

Calculate the fraction of dimers per frame.

# Arguments

  * `smld::BasicSMLD`: SMLD containing all emitters

# Returns

  * `Tuple{Vector{Int}, Vector{Float64}}`: Frame numbers and dimer fractions

# Example

```julia
# Calculate dimer fraction over time
frames, fractions = analyze_dimer_fraction(smld)
plot(frames, fractions, xlabel="Frame", ylabel="Dimer Fraction")
```
