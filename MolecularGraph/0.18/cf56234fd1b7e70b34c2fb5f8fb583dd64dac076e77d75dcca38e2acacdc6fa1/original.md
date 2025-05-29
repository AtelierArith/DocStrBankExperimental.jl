```
inchi(molblock::String; options::String = "", verbose::Bool = false) -> Union{String,Nothing}
inchi(mol::MolGraph; options::String = "", verbose::Bool = false) -> Union{String,Nothing}
```

Generate InChI string from molblock string or molecule.

Options, e.g. "SNon" for 'no stereo information' are specified in https://github.com/mojaie/libinchi/blob/master/INCHIBASE/src/inchiapi.h
