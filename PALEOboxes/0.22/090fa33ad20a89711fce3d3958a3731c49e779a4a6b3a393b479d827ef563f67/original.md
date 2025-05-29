```
VariableAggregatorNamed(modeldata, arrays_idx=1) -> VariableAggregatorNamed
VariableAggregatorNamed(vars, modeldata, arrays_idx=1) -> VariableAggregatorNamed
VariableAggregatorNamed(va::VariableAggregator; ignore_cellranges=false) -> VariableAggregatorNamed
```

Aggregate VariableDomains into nested NamedTuples, with Domain and Variable names as keys and data arrays (from `get_data`) as values.

Any `/` characters in Variable names are replaced with `__` (double underscore)

This provides direct access to Variables by name, and is mostly useful for testing or for small models.

# Fields

  * `vars`: nested NamedTuples (domainname, varname) of VariableDomains
  * `values`: nested NamedTuples (domainname, varname) of data arrays.
