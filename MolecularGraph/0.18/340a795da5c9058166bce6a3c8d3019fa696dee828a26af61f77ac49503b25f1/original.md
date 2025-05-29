```
smilestomol(smiles::AbstractString) -> GraphMol{SmilesAtom,SmilesBond}
```

Parse SMILES string into `GraphMol` object.

The syntax of SMILES in this library follows both Daylight SMILES and OpenSMILES.

# References

1. OpenSMILES Specification http://opensmiles.org/spec/open-smiles.html
2. Daylight Tutorials https://www.daylight.com/dayhtml_tutorials/index.html
