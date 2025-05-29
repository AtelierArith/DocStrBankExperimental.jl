```
bea_table(dataset::String, TableName::String, frequency::String,
    startyear::Int, endyear::Int; user_id = USER_ID) -> BeaTable
```

Return a [`BeaTable`](@ref) with data and metadata for `TableName`.  Pass integer value `0` for both `startyear` and `endyear` to retrieve all available years for the table. The data values are returned in a `DataFrame` accessed through the `data_values` field of the `BeaTable` struct.

The `TableName` argument refers to the API `TableName` parameter value for the requested table.  These can be found using the [`bea_parametervalues`](@ref) method.

Example: to get Table 1.1.6 in the NIPA dataset, quarterly, from 2015 to 2018.

```julia
# User ID stored in ~/.beadatarc
julia> nipa116 = bea_table("NIPA", "T10106", "Q", 2015, 2018)
BEA Table
Dataset:   NIPA
Table No.: 1.1.6
Title:     Real Gross Domestic Product, Chained Dollars
Metric:    Chained Dollars
Units:     Billions of chained (2012) dollars
Frequency: Q
Dates:     2015 - 2018
Revised:   August 29, 2019
```
