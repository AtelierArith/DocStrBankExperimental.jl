```
batch( 
	detectors_array::Vector{<: Detector},
    srcHeights_array::Vector{S},
    srcRhos_array::Vector{S}=[0.0],
    srcRadii_array::Vector{S}=[0.0],
    srcLengths_array::Vector{S}=[0.0],
	ispoint::Bool=true
	)::Vector{String} where S <: Real
```

**same as [`batch(::Detector, ::Vector{Real},::Vector{Real},::Vector{Real},::Vector{Real},::Bool)`](@ref)** but accept a list of detectors `detectors_array`. return a list of paths to the **`CSV`** of files (file for each detector) storing the results.
