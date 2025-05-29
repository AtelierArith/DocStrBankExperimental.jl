BlobLoG stores information about the location of peaks as discovered by `blob_LoG`. It has fields:

  * location: the location of a peak in the filtered image (a CartesianIndex)
  * σ: the value of σ which lead to the largest `-LoG`-filtered amplitude at this location
  * amplitude: the value of the `-LoG(σ)`-filtered image at the peak

Note that the radius is equal to σ√2.

See also: [`blob_LoG`](@ref).
