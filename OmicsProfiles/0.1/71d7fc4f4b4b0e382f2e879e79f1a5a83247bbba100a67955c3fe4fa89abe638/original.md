```
Profile(countmat, omicsname, var, obs; varindex=:genesymbol, obsindex::Symbol=:barcode,
        T=float(eltype(countmat)))
```

Constructor for establishing `AnnotatedProfile` with a `OmicsProfile` inside.

# Arguments

  * `countmat`: The count matrix for given omics and it will be set to key `:count`.
  * `omicsname::Symbol`: The name of given `OmicsProfile`.
  * `var::DataFrame`: The dataframe contains meta information for features or variables.
  * `obs::DataFrame`: The dataframe contains meta information for observations.
  * `varindex::Symbol`: The index of dataframe `var`.
  * `obsindex::Symbol`: The index of dataframe `obs`.
  * `T`: Element type of `countmat`.
