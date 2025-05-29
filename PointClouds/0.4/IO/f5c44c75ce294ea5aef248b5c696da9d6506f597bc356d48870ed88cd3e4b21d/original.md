```
scanner_channel([T], p::PointRecord)
scanner_channel([T], points, inds = :)
```

Obtain the channel/scanner head of a multi-channel system, as an integer between 0 and 3. This is only supported for the PDRFs 6–10 and returns `missing` for the legacy PDRFs 0–5.

See also: [`PointRecord`](@ref)
