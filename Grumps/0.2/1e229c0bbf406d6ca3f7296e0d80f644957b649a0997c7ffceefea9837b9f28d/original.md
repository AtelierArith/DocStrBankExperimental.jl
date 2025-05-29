```
Sources( ;
    consumers   :: Any = nothing, 
    products    :: Any = nothing, 
    marketsizes :: Any = nothing, 
    draws       :: Any = nothing,
)
```

Creates a GrumpsSources object with source type entries where the entries are provided in the optional parameters.

Grumps (potentially) uses four data sources: a data source for consumer-level data, one for product-level data, one for market size information, and one for demographic draws.  See [Spreadsheet formats](@ref) for data layouts. Only the product-level data are required, but are by themselves insufficient.  For instance, for BLP95 one needs information on products, market sizes, and demographics; for the Grumps CLER estimator one needs all four types of data; for a multinomial logit both consumer and product information are needed.  Not all data are needed for all markets.  For instance, it is ok for some estimators for there to be consumer-level data in some markets but not others.

By default, the entries can be nothing, a string, a DataFrame, or a SourceFileType.  If an entry is nothing, it means that no such data is to be used.  If an entry is a string then it is converted to a SourceFileCSV entry with comma delimiter where the string name is the file name.  To use other source file types, create a SourceFileType first.  A DataFrame can be passed, also.  In all cases other than nothing, data will eventually be (converted to) a DataFrame and parsed from that.

The *consumers* variable specifies where consumer-level data can be found, the *products* variable is for the product-level data, *marketsizes* is for market sizes, and *draws* is for demographic draws.

Use the [`Variables()`](@ref) method to specify the way the data sources are formatted and the specification to estimate.
