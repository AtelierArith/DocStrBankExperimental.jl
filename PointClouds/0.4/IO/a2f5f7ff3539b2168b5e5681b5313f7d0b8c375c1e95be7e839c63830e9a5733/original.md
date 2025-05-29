```
intensity(p::PointRecord)
intensity(points, inds = :)
```

Obtain the intensity of the pulse return, normalized such that the dynamic range of the sensor is represented by the range from 0 to 1.

See also: [`PointRecord`](@ref), [`color_channels`](@ref), [`return_number`](@ref), [`return_count`](@ref), [`waveform_packet`](@ref)
