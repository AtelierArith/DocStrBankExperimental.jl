```
lattice_vectors(r::RectangularLattice)
```

Returns the Bravais lattice vectors for a Rectangular lattice as a Tuple of Tuples containing floats.

The vectors are defined as:

  * 𝐚₁ = (1.0, 0.0)
  * 𝐚₂ = (0.0, `r.aspect_ratio`), where `aspect_ratio` is a `Float64`.
