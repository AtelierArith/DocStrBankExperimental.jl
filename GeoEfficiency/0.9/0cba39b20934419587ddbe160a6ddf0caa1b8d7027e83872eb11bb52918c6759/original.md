```
batch(
	detector_info_array::Matrix{S},
	srcHeights_array::Vector{S},
	srcRhos_array::Vector{S}=[0.0],
	srcRadii_array::Vector{S}=[0.0],
	srcLengths_array::Vector{S}=[0.0],
	ispoint::Bool=true
	)::Vector{String} 	where S <: Real
```

**same as [`batch(::Vector{Detector}, ::Vector{Real},::Vector{Real},::Vector{Real},::Vector{Real},::Bool)`](@ref)** but provide batch calculation of the  `geometrical efficiency` for the detector in the `detector_info_array` after applying `getDetectors`. return a list of paths to the **`CSV`** of files (file for each detector) storing the results.
