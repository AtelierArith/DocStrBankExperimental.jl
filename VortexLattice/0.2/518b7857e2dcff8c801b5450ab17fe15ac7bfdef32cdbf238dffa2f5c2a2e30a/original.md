```
lifting_line_geometry(grids, xc=0.25)
```

Construct a lifting line representation of the surfaces in `grids` at the normalized chordwise location `xc`.  Return the lifting line coordinates and chord lengths.

# Arguments

  * `grids`: Vector with length equal to the number of surfaces.  Each element of  the vector is a grid with shape (3, nc, ns) which defines the discretization  of a surface into panels. `nc` is the number of chordwise panels and `ns` is  the number of spanwise panels.
  * `xc`: Normalized chordwise location of the lifting line from the leading edge.  Defaults to the quarter chord

# Return Arguments:

  * `r`: Vector with length equal to the number of surfaces, with each element  being a matrix with size (3, ns+1) which contains the x, y, and z coordinates  of the resulting lifting line coordinates
  * `c`: Vector with length equal to the number of surfaces, with each element  being a vector of length `ns+1` which contains the chord lengths at each  lifting line coordinate.
