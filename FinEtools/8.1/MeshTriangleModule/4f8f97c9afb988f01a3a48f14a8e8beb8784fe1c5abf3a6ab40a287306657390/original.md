```
T3annulus(rin::T, rex::T, nr::IT, nc::IT, angl::T, orientation::Symbol=:a)
```

Mesh of an annulus segment.

Mesh of an annulus segment, centered at the origin, with internal radius `rin`, and  external radius `rex`, and  development angle `angl` (in radians). Divided into elements: nr, nc in the radial and circumferential direction respectively.
