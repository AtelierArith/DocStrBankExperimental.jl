Create array of structures of SpeciesRxnMap. The SpeciesRxnMap is a  composit structure of species_id in participating reactions and the stoichiometric coefficients

# Usage

```
species_rxn_map(gas_species,sm)
```

  * gas_species::Array{String,1} :  list of gas phase species
  * sm::SurfaceMechanism : SurfaceMechanism composite type
