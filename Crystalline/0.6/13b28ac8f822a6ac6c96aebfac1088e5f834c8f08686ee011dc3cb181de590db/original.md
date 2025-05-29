```julia
mulliken(pgir::Crystalline.PGIrrep{D}) -> String

```

Return the Mulliken label of a point group irrep `pgir`.

## Notes

This functionality is a simple mapping between the tabulated CDML point group irrep labels and associated Mulliken labels [^1], using the listings from the Bilbao Crystallographic Database [^2].

Ignoring subscript, the rough rules associated with assignment of Mulliken labels are:

1. **Irrep dimensionality**: 

      * **1D irreps**: if a real irrep, assign A or B (B if antisymmetric under a principal  rotation); if a complex irrep, assigned label ¹E or ²E.
      * **2D irreps**: assign label E.
      * **3D irreps**: assign label T.
2. ***u* and *g* subscripts**: if the group contains inversion, indicate whether irrep is symmetric (g ~ gerade) or antisymmetric (u ~ ungerade) under inversion.
3. **Prime superscripts**: if the group contains a mirror *m* aligned with a principal  rotation axis, but does *not* contain inversion, indicate whether irrep is symmetric (′)  or antisymmetric (′′) under this mirror.
4. **Numeral subscripts**: the rules for assignment of numeral subscripts are too complicated in general - and indeed, we are unaware of a general coherent rule – to describe here.

## References

[^1]: Mulliken, Report on Notation for the Spectra of Polyatomic Molecules,    [J. Chem. Phys. *23*, 1997 (1955)](https://doi.org/10.1063/1.1740655).

[^2]: Bilbao Crystallographic Database's   [Representations PG program](https://www.cryst.ehu.es/cgi-bin/cryst/programs/representations_point.pl?tipogrupo=spg).
