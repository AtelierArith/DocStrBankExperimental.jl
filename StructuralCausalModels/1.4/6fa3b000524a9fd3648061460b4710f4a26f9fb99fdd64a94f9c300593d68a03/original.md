# DAG

Directed acyclic graph struct

### Struct

```julia
DAG(
* `name::AbstractString`                    : Name for the DAG object
* `d::OrderedDictOrNothing`                 : DAG definition as an OrderedDict
* `a::NamedArrayOrNothing`                  : Adjacency matrix
* `e::NamedArrayOrNothing`                  : Edge matrix
* `s::NamedArrayOrNothing`                  : Covariance matrix
* `df::DataFrameOrNothing`                  : Variable observations
* `vars::Vector{Symbol}`                    : Names of variables in DAG
)
```

Part of API, exported.
