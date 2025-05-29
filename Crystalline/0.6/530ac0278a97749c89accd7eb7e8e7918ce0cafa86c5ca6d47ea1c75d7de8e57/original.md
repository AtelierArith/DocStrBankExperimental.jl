```
pgirreps(iuclab::String, ::Val{D}=Val(3); mullikken::Bool=false) where D ∈ (1,2,3)
pgirreps(iuclab::String, D; mullikken::Bool=false)
```

Return the (crystallographic) point group irreps of the IUC label `iuclab` of dimension `D` as a `Vector{PGIrrep{D}}`.

See `Crystalline.PG_IUC2NUM[D]` for possible IUC labels in dimension `D`.

## Notation

The irrep labelling follows the conventions of CDML [^1] [which occasionally differ from those in e.g. Bradley and Cracknell, *The Mathematical Theory of Symmetry in Solids*  (1972)].

To use Mulliken ("spectroscopist") irrep labels instead, set the keyword argument `mulliken = true` (default, `false`). See also [`mulliken`](@ref).

## Data sources

The data is sourced from the Bilbao Crystallographic Server [^2]. If you are using this  functionality in an explicit fashion, please cite the original reference [^3].

## References

[^1]: Cracknell, Davies, Miller, & Love, Kronecher Product Tables 1 (1979).

[^2]: Bilbao Crystallographic Database's   [Representations PG program](https://www.cryst.ehu.es/cgi-bin/cryst/programs/representations_point.pl?tipogrupo=spg).

[^3]: Elcoro et al.,    [J. of Appl. Cryst. **50**, 1457 (2017)](https://doi.org/10.1107/S1600576717011712)
