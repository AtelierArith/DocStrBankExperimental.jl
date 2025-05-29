```
read_10x(path; make_unique=true, omicsname=:RNA, varnames=[:ensembleid, :genesymbol],
    obsnames=[:barcode], varindex=:genesymbol, obsindex=:barcode)
```

Reads 10x dataset from `path` and returns an `AnnotatedProfile`.

# Arguments

  * `path::AbstractString`: The path to 10x dataset folder.
  * `make_unique::Bool`: To make `varindex` unique or not if given `varindex` is not unique.
  * `omicsname::Symbol`: The name of given sequencing data.
  * `varnames::AbstractVector`: The header or column names of feature file.
  * `obsnames::AbstractVector`: The header or column names of barcode file.
  * `varindex::Symbol`: The index of dataframe `var`.
  * `obsindex::Symbol`: The index of dataframe `obs`.

# Examples

```jldoctest
julia> using SnowyOwl

julia> prof = read_10x(SnowyOwl.Dataset.pbmc3k_folder(), varindex=:ensembleid)
AnnotatedProfile (nobs = 2700):
    obs: barcode
RNA => OmicsProfile (nvar = 32738):
    var: ensembleid, genesymbol
    layers: count
```
