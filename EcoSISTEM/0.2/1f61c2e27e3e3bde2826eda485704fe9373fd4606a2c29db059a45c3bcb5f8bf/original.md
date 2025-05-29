```
CachedEcosystem{Part <: AbstractAbiotic, SL <: SpeciesList,
    TR <: AbstractTraitRelationship} <: AbstractEcosystem{Part, SL, TR}
```

CachedEcosystem houses the same information as Ecosystem (see ?Ecosystem), but holds the time period abundances as a CachedGridLandscape, so that they may be present or missing.
