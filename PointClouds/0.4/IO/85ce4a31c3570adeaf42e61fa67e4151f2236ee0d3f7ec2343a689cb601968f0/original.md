```
intensity(Integer, p::PointRecord)
intensity(Integer, points, inds = :)
```

Obtain the “raw” intensity of a point record as a unsigned 16-bit integer. Values should be normalized such that the dynamic range of the sensor corresponds to the range from 0 to 65535.

See also: [`PointRecord`](@ref), [`color_channels`](@ref), [`return_number`](@ref), [`return_count`](@ref), [`waveform_packet`](@ref)
