```
check_for_duplicates(log_volume_km3_vector::Union{Float64,Vector{Float64}}, InitialConc_H2O_vector::Union{Float64,Vector{Float64}}, InitialConc_CO2_vector::Union{Float64,Vector{Float64}}, log_vfr_vector::Union{Float64,Vector{Float64}}, depth_vector::Union{Float64,Vector{Float64}})::Nothing
```

This function checks if any of the input arrays contain duplicate elements. If duplicates are found, it raises an error indicating which arguments have duplicates.

  * This function is used within the `chamber` function
