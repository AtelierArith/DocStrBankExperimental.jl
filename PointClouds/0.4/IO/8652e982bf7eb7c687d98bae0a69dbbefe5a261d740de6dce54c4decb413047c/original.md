```
return_count([T], p::PointRecord)
return_count([T], points, inds = :)
```

Obtain the total number of returns produced by the laser pulse. The value is between 1 and 15 for the PDRFs 6–10, and between 1 and 5 for the legacy PDRFs 0–5.

See also: [`PointRecord`](@ref), [`intensity`](@ref), [`return_number`](@ref), [`waveform_packet`](@ref)
