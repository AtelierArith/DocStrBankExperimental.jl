Encodes a chemical species by wrapping an integer that represents the atomic  number, the number of protons, and additional name as max 4 characters.

The name variable can be used as atom name in PDB format or some other way to mark same kind of atoms from one another.

Constructors for standard chemical elements

```julia
ChemicalSpecies(Z::Integer)
ChemicalSpecies(sym::Symbol) 
# for example 
ChemicalSpecies(:C)
ChemicalSpecies(6)
```

Constructors for isotopes 

```julia
# standard carbon = C-12
ChemicalSpecies(:C)
ChemicalSpecies(:C; n_neutrons = 6)

# three equivalent constructors for C-13
ChemicalSpecies(:C; n_neutrons = 7)
ChemicalSpecies(6; n_neutrons = 7)
ChemicalSpecies(:C13)
# deuterium
ChemicalSpecies(:D)
```

Constructors for names

```julia
ChemicalSpecies(:C; atom_name=:MyC)
ChemicalSpecies(:C13; atom_name=:MyC)
```

Comparisons with different isotopes and names

```julia
# true
ChemicalSpecies(:C13) == ChemicalSpecies(:C)

# false
ChemicalSpecies(:C12) == ChemicalSpecies(:C13)

# true
ChemicalSpecies(:C; atom_name=:MyC) == ChemicalSpecies(:C)

# true
ChemicalSpecies(:C12; atom_name=:MyC) == ChemicalSpecies(:C12)

# false
ChemicalSpecies(:C; atom_name=:MyC) == ChemicalSpecies(:C12)

# true
ChemicalSpecies(:C12; atom_name=:MyC) == ChemicalSpecies(:C)

# true
ChemicalSpecies(:C; atom_name=:MyC) == ChemicalSpecies(:C12; atom_name=:MyC)
```
