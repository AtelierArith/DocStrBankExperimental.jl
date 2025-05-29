```
remove_hydrogens!(q::MolGraph) -> Nothing
```

Remove hydrogens from the molecular query. 

Should be applied after `specialize_nonaromatic!`. This function is intended for generalization of PAINS query in PubChem dataset.
