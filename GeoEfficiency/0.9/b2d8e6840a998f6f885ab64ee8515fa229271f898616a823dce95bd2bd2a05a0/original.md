```
batch(
	detector::Detector,
	srcHeights_array::Vector{S},
	srcRhos_array::Vector{S}=[0.0],
	srcRadii_array::Vector{S}=[0.0],
	srcLengths_array::Vector{S}=[0.0],
	ispoint::Bool=true
	)::String 	where S <: Real
```

provide batch calculation of the `geometrical efficiency` for the detector `detector`.  results are saved on a **`CSV`**  file named after the detector.  the **`CSV`**  file by default found in **`/home/terasaki/GeoEfficiency/results`**. this method return the actual  path to the **`CSV`** file.  also a log of the results are displayed on the `console`.

  * `srcHeights_array`: list of source heights to feed to batch.
  * `srcRhos_array`: list of source off-axis distances to feed to batch.
  * `srcRadii_array`: list of source radii to feed to batch.
  * `srcLengths_array`: list of source lengths to feed to batch.

A set of sources is constructed of every valid **combination** of parameter in the `srcRhos_array`, `srcRadii_array` and `srcLengths_array` arrays with conjunction with `ispoint`.

!!! warning
      * If `ispoint` is `true` the source type is a point source and the parameters   in `srcRadii_array` and `srcLengths_array` arrays is completely ignored.
      * If `ispoint` is `false` the parameters in srcRhos_array is completely ignored.

