```
OceanGrid(elon::T, elat::U, edepth::V; R=6371.0u"km") where {T<:TU, U<:TU, V<:TU}
```

Returns an `OceanRectilinearGrid` with boxes whose edges are defined by the `elon`, `elat`, and `edepth` vectors. The globe radius can be changed with the keyword `R` (default value 6371 km) The 3D array of wet boxes, `wet3D` is true everywhere by default.
