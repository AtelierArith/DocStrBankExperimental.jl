Encodes a chemical species by wrapping an integer that represents the atomic  number, the number of protons, and additional unspecified information as a `UInt32`. 

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
