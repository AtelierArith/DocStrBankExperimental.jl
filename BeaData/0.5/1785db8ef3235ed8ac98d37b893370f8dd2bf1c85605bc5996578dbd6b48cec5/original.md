```
bea_parametervalues(dataset::String, param_name:: String;
    user_id = USER_ID) -> DataFrame
```

Return a `DataFrame` of permissible values for `param_name`, with descriptions.

Example:

```julia
# User ID stored in ~/.beadatarc
julia> bea_parametervalues("NIPA", "TableName");

julia> show(ans[1:3, :])
3×2 DataFrame
│ Row │ Value  │ Description                                                                              │
│     │ String │ String                                                                                   │
├─────┼────────┼──────────────────────────────────────────────────────────────────────────────────────────┤
│ 1   │ T10101 │ Table 1.1.1. Percent Change From Preceding Period in Real Gross Domestic Product (A) (Q) │
│ 2   │ T10102 │ Table 1.1.2. Contributions to Percent Change in Real Gross Domestic Product (A) (Q)      │
│ 3   │ T10103 │ Table 1.1.3. Real Gross Domestic Product, Quantity Indexes (A) (Q)                       │

```
