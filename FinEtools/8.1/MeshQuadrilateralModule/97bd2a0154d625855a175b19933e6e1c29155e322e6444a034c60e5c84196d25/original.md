```
Q4annulus(rin::T, rex::T, nr::IT, nc::IT, Angl::T) where {T<:Number, IT<:Integer}
```

Mesh of an annulus segment.

Mesh of an annulus segment, centered at the origin, with internal radius `rin`, and  external radius `rex`, and  development angle `Angl` (in radians). Divided into elements: nr, nc in the radial and circumferential direction respectively.
