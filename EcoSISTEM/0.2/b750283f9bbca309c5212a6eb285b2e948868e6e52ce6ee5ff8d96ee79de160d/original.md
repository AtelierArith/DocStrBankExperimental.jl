```
Ecosystem{Part <: AbstractAbiotic} <:
   AbstractEcosystem{Part, SL, TR}
```

Ecosystem houses information on species and their interaction with their environment. For species, it holds abundances and locations, `abundances`, as well as properties such as trait information, `spplist`, and movement types, `lookup`. For environments, it provides information on environmental conditions and available resources,`abenv`. Finally, there is a slot for the relationship between the environment and the characteristics of the species, `relationship`.
