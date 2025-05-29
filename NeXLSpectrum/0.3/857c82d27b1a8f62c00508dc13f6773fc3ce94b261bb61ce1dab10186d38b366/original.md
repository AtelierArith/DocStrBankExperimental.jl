```
integrate(spec::Spectrum, channels::AbstractUnitRange{<:Integer})
integrate(spec::Spectrum, energyRange::StepRangeLen{Float64})
```

Sums all the counts in the specified channels.  No background correction.  The `energyRange` version includes the fractional contributions from partial channels when the energies don't perfectly map to channels.

```
integrate(spec::Spectrum, back1::AbstractUnitRange{<:Integer}, peak::AbstractUnitRange{<:Integer}, back2::AbstractUnitRange{<:Integer})::UncertainValue
integrate(spec::Spectrum, back1::StepRangeLen{Float64}, peak::StepRangeLen{Float64}, back2::StepRangeLen{Float64})::UncertainValue
```

Sums all the counts in the specified channels with background correction using the background intervals.

```
integrate(spec::Spectrum)
```

Total integral of all counts from the LLD to the beam energy
