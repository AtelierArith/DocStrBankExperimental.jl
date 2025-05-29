```
isobars_rt_table(ion::AbstractChemical, lib::AbstractVector{T}; rt_tol = 0.3, mz_tol = crit(0.01, 20e-6))
isobars_rt_table(exp::Vector, lib::AbstractVector{T}; kwargs...)
isobars_rt_table(exp::Table, lib::AbstractVector{T}; expid = true, expchemical = :AdductIon, expmz = :MZ, exprt = :RT, rt_tol = 0.3, mz_tol = crit(0.01, 20e-6))
isobars_rt_table(ion::AbstractChemical, lib::Table; libid = true, libchemical = :AdductIon, libmz = :MZ, librt = :RT, rt_tol = 0.3, mz_tol = crit(0.01, 20e-6))
isobars_rt_table(exp::Vector, lib::Table; libid = true, libchemical = :AdductIon, libmz = :MZ, librt = :RT, rt_tol = 0.3, mz_tol = crit(0.01, 20e-6))
isobars_rt_table(exp::Table, lib::Table; expid = true, expchemical = :AdductIon, expmz = :MZ, exprt = :RT, libid = true, libchemical = :AdductIon, libmz = :MZ, librt = :RT, rt_tol = 0.3, mz_tol = crit(0.01, 20e-6))
```

Return a `Table` such that all rows representing an ion from `lib` which are isobaric to `ion` or ions from `exp` within specific tolerance of rt and mz. 

Tolerance can be a number or criteria, representing maximum allowed difference. For criteria with multiple allowed intervals, lying in any of them is considered to fulfill the criteria. 

Keyword arguments `libchemical`, `libmz`, and `librt` specify the columns of `AdductIon` objects, m/z values, and rt values from `lib`. 

Keyword arguments `expchemical`, `expmz`, and `exprt` specify the columns of `AdductIon` objects, m/z values, and rt values from `exp`. 

Keyword arguments `libid` and `expid` determine whether creates columns to store row id of `lib` or `exp`.
