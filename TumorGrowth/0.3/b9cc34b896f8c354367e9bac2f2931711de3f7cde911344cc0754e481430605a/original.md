```
patient_data()
```

Return, in row table form, the lesion measurement data collected in Laleh et al. [(2022)](https://doi.org/10.1371/journal.pcbi.1009822) "Classical mathematical models for prediction of response to chemotherapy and immunotherapy", *PLOS Computational Biology*.

Each row represents all measurements for a single lesion for a unique patient.

```julia
record = first(patient_data())

julia> record.Pt_hashID # patient identifier
"0218075314855e6ceacca856fcd4c737-S1"

julia> record.T_weeks # measure times, in weeks
7-element Vector{Float64}:
  0.1
  6.0
 12.0
 17.0
 23.0
 29.0
 35.0

julia> record.Lesion_normvol # all volumes measured, normalised by dataset max
7-element Vector{Float64}:
 0.000185364052636979
 0.00011229838600811
 8.4371439525252e-5
 8.4371439525252e-5
 1.05464299406565e-5
 2.89394037571615e-5
 8.4371439525252e-5
```

See also [`flat_patient_data`](@ref).
