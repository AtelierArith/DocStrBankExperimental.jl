```
bea_datasets(;user_id::String = USER_ID) -> DataFrame
```

Return a `DataFrame` of names and descriptions for datasets accessible through the BEA data API.

Example:

```julia
# User ID stored in ~/.beadatarc
julia> bea_datsets();

julia> show(ans[1:3, :])
3×2 DataFrames.DataFrame
│ Row │ DatasetName        │ Description                          │
│     │ String             │ String                               │
├─────┼────────────────────┼──────────────────────────────────────┤
│ 1   │ NIPA               │ Standard NIPA tables                 │
│ 2   │ NIUnderlyingDetail │ Standard NI underlying detail tables │
│ 3   │ MNE                │ Multinational Enterprises            │
```
