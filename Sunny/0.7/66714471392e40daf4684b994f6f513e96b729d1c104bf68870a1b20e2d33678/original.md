An object describing a crystallographic unit cell and its space group symmetry. Constructors are as follows:

```
Crystal(filename; override_symmetry=false, symprec=nothing)
```

Reads the crystal from a `.cif` file located at the path `filename`. If `override_symmetry=true`, the spacegroup will be inferred based on atom positions and the returned unit cell may be reduced in size. For an mCIF file, the return value is the magnetic supercell, unless `override_symmetry=true`. If a precision for spacegroup symmetries cannot be inferred from the CIF file, it must be specified with `symprec`. The `latvecs` field of the returned `Crystal` will be in units of angstrom.

```
Crystal(latvecs, positions; types=nothing, symprec=1e-5)
```

Constructs a crystal from the complete list of atom positions `positions`, with coordinates (between 0 and 1) in units of lattice vectors `latvecs`. Spacegroup symmetry information is automatically inferred using the [Spglib package](https://github.com/spglib/spglib) [1]. The optional parameter `types` is a list of strings, one for each atom, and can be used to break symmetry-equivalence between atoms.

```
Crystal(latvecs, positions, spacegroup; types=nothing, choice=nothing, symprec=1e-5)
```

Builds a crystal using the symmetries of a `spacegroup`. One representative atom must be specified for each occupied Wyckoff. The `spacegroup` may be specified as a number 1..230 or as a string, e.g., Hermann–Mauguin or Hall symbol. If only a spacegroup number is provided, the ITA standard setting [2] will be employed, consistent with conventions from the [Bilbao crystallographic server](https://www.cryst.ehu.es). If a spacegroup symbol is provided that allows for multiple ITA settings, the possible disambiguations will be included in an error message, and may involve a `choice` string.

# Examples

```julia
# Read a Crystal from a .cif file
Crystal("filename.cif")

# Build a BCC crystal in the conventional cubic unit cell by specifying both
# atoms. The spacegroup 229 is inferred.
latvecs = lattice_vectors(1, 1, 1, 90, 90, 90)
positions = [[0, 0, 0], [1/2, 1/2, 1/2]]
Crystal(latvecs, positions)

# Build a CsCl crystal (two simple cubic sublattices). Because of the distinct
# atom types, the spacegroup number 221 is now inferred.
types = ["Na", "Cl"]
cryst = Crystal(latvecs, positions; types)

# Build a diamond cubic crystal from its spacegroup number 227 and a single
# atom position belonging to Wyckoff 8a.
positions = [[1/8, 1/8, 1/8]]
cryst = Crystal(latvecs, positions, 227)

# Build an equivalent crystal using a different origin choice.
positions = [[0, 0, 0]]
cryst = Crystal(latvecs, positions, 227; choice="1")
```

See also [`lattice_vectors`](@ref).

## References

1. [A. Togo, K. Shinohara, I. Tanaka, *Spglib: a software library for crystal symmetry search* (2018) [arXiv:1808.01590]](https://arxiv.org/abs/1808.01590).
2. [International Tables of Crystallography, Volume A (2016)](https://doi.org/10.1107/97809553602060000114).
