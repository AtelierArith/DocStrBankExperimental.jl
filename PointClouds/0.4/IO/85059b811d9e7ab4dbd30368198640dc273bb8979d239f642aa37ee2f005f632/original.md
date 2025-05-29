```
waveform_packet(p::PointRecord)
waveform_packet(points, inds = :)
```

Obtain the raw waveform packet of a point record for PDRFs 4/5/9/10, or `missing` if the PDRFs does not include waveform packets. Note that PointClouds.jl currently has very limited functionality for handling waveform data.

See also: [`PointRecord`](@ref), [`intensity`](@ref), [`return_number`](@ref), [`return_count`](@ref)
