```
spacegroup(sgnum::Integer, ::Val{D}=Val(3))
spacegroup(sgnum::Integer, D::Integer)          --> SpaceGroup{D}
```

Return the space group symmetry operations for a given space group number `sgnum` and  dimensionality `D` as a `SpaceGroup{D}`. The returned symmetry operations are specified relative to the conventional basis vectors, i.e. are not necessarily primitive (see [`centering`](@ref)). If desired, operations for the primitive unit cell can subsequently be generated using  [`primitivize`](@ref) or [`Crystalline.reduce_ops`](@ref).

The default choices for the conventional basis vectors follow the conventions of the Bilbao Crystallographic Server (or, equivalently, the International Tables of Crystallography),  which are:

  * Unique axis *b* (cell choice 1) for monoclinic space groups.
  * Obverse triple hexagonal unit cell for rhombohedral space groups.
  * Origin choice 2: inversion centers are placed at (0,0,0). (relevant for certain centrosymmetric space groups with two possible choices; e.g., in the orthorhombic, tetragonal or cubic crystal systems).

See also [`directbasis`](@ref).

## Data sources

The symmetry operations returned by this function were originally retrieved from the [Bilbao Crystallographic Server, SPACEGROUP GENPOS](https://www.cryst.ehu.es/cryst/get_gen.html). The associated citation is: ([Aroyo et al., Z. Kristallogr. Cryst. Mater. **221**, 15 (2006).](https://doi.org/10.1524/zkri.2006.221.1.15)).
