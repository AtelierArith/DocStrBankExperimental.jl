```
pmap2df(pmap::Pmap) -> DataFrame
```

Convert a phenotype map object (`Pmap`) into a DataFrame.

# Arguments

  * `pmap`: A genetic map object containing mapping information.  This object should conform to the expected structure, which includes:

      * `chr`: An array of chromosome identifiers.
      * `marker_name`: A nested array of marker names organized by chromosome.
      * `pos`: A nested array of marker positions, also organized by chromosome.

# Returns

  * `DataFrame`: A DataFrame representing the phenotypic map data, with columns

for marker names (`Locus`), chromosome identifiers (`Chr`), and  marker positions (`Pos`).
