```
irrfbz_path(sgnum::Integer, Rs, [::Union{Val(D), Integer},]=Val(3))  -->  ::KPath{D}
```

Returns a **k**-path (`::KPath`) in the (primitive) irreducible Brillouin zone for a space group with number `sgnum`, (conventional) direct lattice vectors `Rs`, and dimension `D`. The path includes all distinct high-symmetry lines and points as well as relevant parts of the Brillouin zone boundary.

The dimension `D` (1, 2, or 3) is specified as the third input argument, preferably as a static `Val{D}` type parameter (or, type-unstably, as an `<:Integer`). Defaults to `Val(3)`.

`Rs` refers to the direct basis of the conventional unit cell, i.e., not the primitive  direct basis vectors. The setting of `Rs` must agree with the conventional setting choices in the International Tables of Crystallography, Volume A (the "ITA conventional setting"). If `Rs` is a subtype of a `StaticVector` or `NTuple`, the dimension can be inferred from its (static) size; in this case, this dimension will take precedence (i.e. override, if different) over any dimension specified in the third input argument.

## Notes

  * The returned **k**-points are given in the basis of the **primitive** reciprocal basis in the CDML setting. To obtain the associated transformation matrices between the ITA conventional setting and the CDML primitive setting, see `primitivebasismatrix` of Bravais.jl](https://thchr.github.io/Crystalline.jl/stable/bravais/) (or, equivalently, the relations defined Table 2 of [^1]). To transform to a Cartesian basis, see [`cartesianize!`](@ref).
  * To interpolate a `KPath`, see [`interpolate(::KPath, ::Integer)`](@ref) and [`splice(::KPath, ::Integer)`](@ref).
  * All paths currently assume time-reversal symmetry (or, equivalently, inversion symmetry). If neither are present, include the "inverted" -**k** paths manually.

## Data and referencing

3D paths are sourced from the SeeK-path publication: please cite the original work [^2].

## References

[^1]: Aroyo et al., [Acta Cryst. A70, 126 (2014)](https://doi.org/10.1107/S205327331303091X).

[^2]: Hinuma, Pizzi, Kumagai, Oba, & Tanaka, *Band structure diagram paths based on   crystallography*, [Comp. Mat. Sci. **128**, 140 (2017)](http://dx.doi.org/10.1016/j.commatsci.2016.10.015).
