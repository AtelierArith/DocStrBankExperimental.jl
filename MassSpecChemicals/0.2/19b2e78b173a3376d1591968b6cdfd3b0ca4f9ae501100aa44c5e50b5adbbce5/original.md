```
isobars_rt(ion::AbstractChemical, lib::AbstractVector{T}; rt_tol = 0.3, mz_tol = crit(0.01, 20e-6))
isobars_rt(ion::AbstractChemical, lib::Table; libchemical = :AdductIon, libmz = :MZ, librt = :RT, rt_tol = 0.3, mz_tol = crit(0.01, 20e-6))
```

Return a subvector of `lib` such that all elements are isobaric to `ion` within specific tolerance of rt and mz. 

Keyword arguments `libchemical`, `libmz`, and `librt` specify the columns of `AdductIon` objects, m/z values, and rt values. 

Tolerance can be a number or criteria, representing maximum allowed difference. For criteria with multiple allowed intervals, lying in any of them is considered to fulfill the criteria. 
