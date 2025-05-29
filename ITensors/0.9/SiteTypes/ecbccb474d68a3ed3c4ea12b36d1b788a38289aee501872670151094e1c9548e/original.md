```
op(opname::String, s::Index; kwargs...)
```

Return an ITensor corresponding to the operator named `opname` for the Index `s`. The operator is constructed by calling an overload of either the `op` or `op!` methods which take a `SiteType` argument that corresponds to one of the tags of the Index `s` and an `OpName"opname"` argument that corresponds to the input operator name.

Operator names can be combined using the `"*"` symbol, for example `"S+*S-"` or `"Sz*Sz*Sz"`. The result is an ITensor made by forming each operator then contracting them together in a way corresponding to the usual operator product or matrix multiplication.

The `op` system is used by the OpSum system to convert operator names into ITensors, and can be used directly such as for applying operators to MPS.

# Example

```julia
s = Index(2, "Site,S=1/2")
Sz = op("Sz", s)
```

You can see all of the operator names defined for the site types included with ITensor [here](https://docs.itensor.org/ITensorMPS/stable/IncludedSiteTypes.html). Note that some site types such as "S=1/2" and "Qubit" are aliases for each other and share operator definitions.
