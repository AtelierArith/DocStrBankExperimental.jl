```
setinvalid_nongrowingseason!(df, tGPP; kwargs...)
```

Set non-growseason to false in :valid column.

# Arguments

  * `df`: DataFrame with columns `:GPP` and `:datetime`
  * `tGPP`: scalar threshold of daily GPP (see [`get_growingseason`](@ref))

optional:

  * `update_GPPd`: set to true additionally update `:GPPd_smoothed` column to results from [`get_growingseason`](@ref)
  * and others passed to [`get_growingseason`](@ref)

# Value

df with modified columns :valid and if  `:GPPd_smoothed`,  where all non-growing season records are set to false.
