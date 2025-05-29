```
ProbabilityDensity <: EnergyMap
```

An energy map based on probability density, a measure based on the differences among the pdfs of $Z_i$. Since we do not know the true density functions of the coefficients, the PDFs are estimated using the Average Shifted Histogram (ASH).

**See also:** [`EnergyMap`](@ref), [`TimeFrequency`](@ref), [`Signatures`](@ref)
