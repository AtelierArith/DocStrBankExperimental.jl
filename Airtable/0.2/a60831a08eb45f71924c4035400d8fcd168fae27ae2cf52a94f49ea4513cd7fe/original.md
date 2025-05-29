```
AirRecord(id::String, table::AirTable, fields::NamedTuple)
```

A wrapper for an [Airtable Record](https://support.airtable.com/hc/en-us/articles/360021333094-Getting-started-tables-records-and-fields), containing its unique identifier, parent [`AirTable`](@ref), and values for any stored fields in a NamedTuple.

Typically, you won't crete these on your own, but they will be returned from API queries.

Field values can be accessed using [`getindex`](@ref `Base.getindex(::AirRecord, ::Symbol)`).
