```
OrdinalIndependenceCor <: CorStruct
```

Type that represents a GEE working correlation structure in which the ordinal observations within a group are modeled as being independent. Each ordinal observation is converted to a set of binary indicators, and the indicators derived from a common ordinal value are modeled as correlated, with the correlations determined from the marginal means.
