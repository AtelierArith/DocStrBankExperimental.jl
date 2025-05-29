```
getDetectors(detector_info_array::Matrix{<:Real}, 
				 detectors_array::Vector{<:Detector} = Detector[]; 
				 						   console_FB=true)::Vector{Detector}
```

return `detectors_array` as Vector{Detector}, after extending it with the successfully converted detectors. while,  attempt to convert detectors from the information in `detector_info_array`. 

!!! note
    if `console_FB` argument is set to true , the function will call `getDetectors()` to take input from the `console` if the `detector_info_array` is empty or contain no numerical element.

