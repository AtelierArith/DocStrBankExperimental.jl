```
bea_parameterlist(dataset::String; user_id = USER_ID) -> DataFrame
```

Return a `DataFrame` of parameter names and attributes for `dataset`.

Example:

```julia
# User ID stored in ~/.beadatarc
julia> bea_parameterlist("NIPA")
5×3 DataFrames.DataFrame. Omitted printing of 1 columns
│ Row │ ParameterName │ ParameterDescription                                           │
│     │ String        │ String                                                         │
├─────┼───────────────┼────────────────────────────────────────────────────────────────┤
│ 1   │ Frequency     │ A - Annual, Q-Quarterly, M-Monthly                             │
│ 2   │ ShowMillions  │ A flag indicating that million-dollar data should be returned. │
│ 3   │ TableID       │ The standard NIPA table identifier                             │
│ 4   │ TableName     │ The new NIPA table identifier                                  │
│ 5   │ Year          │ List of year(s) of data to retrieve (X for All)                │
```
