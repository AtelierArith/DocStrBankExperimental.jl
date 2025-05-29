```julia
findchemical(chemicals, fchem::PetroBase.Chemical) -> Any

```

Finds the first index of 'fChem' in the 'chem' array. Returns 0 if 'fChem' isnt present. Best used with arrays of unique 'Chemical' variables.
