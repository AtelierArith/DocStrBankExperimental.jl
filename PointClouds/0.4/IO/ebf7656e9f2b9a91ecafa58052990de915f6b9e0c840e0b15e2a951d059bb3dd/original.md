```
return_number([T], p::PointRecord)
return_number([T], points, inds = :)
```

Obtain which return of the laser pulse produced the point data record. The value is between 1 and 15 for the PDRFs 6–10, and between 1 and 5 for the legacy PDRFs 0–5.

See also: [`PointRecord`](@ref), [`intensity`](@ref), [`return_count`](@ref), [`waveform_packet`](@ref)
