```
checkerboard!(c::Cell{T,S}, pixsize, rows::Integer, alt, meta::Meta=GDSMeta()) where {T,S}
```

In cell `c`, generate a checkerboard pattern suitable for contrast curve measurement, or getting the base dose for PEC.

  * `pixsize`: length of one side of a square
  * `rows`: number of rows == number of columns
  * `alt`: the square nearest `Point(zero(T), zero(T))` is filled (unfilled) if `false` (`true`). Use this to create a full tiling of the checkerboard, if you wish.
