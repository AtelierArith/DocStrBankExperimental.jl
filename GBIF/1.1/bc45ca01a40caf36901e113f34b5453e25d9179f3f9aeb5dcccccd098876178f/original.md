**List of occurrences and metadata**

This type has actually very few information: the `query` field stores the query parameters. This type is mutable and fully iterable.

The `occurrences` field is pre-allocated, meaning that it will contain `#undef` elements up to the total number of hits on GBIF. When iterating, this is taken care of automatically, but this needs to be accounted for if writing code that accesses this field directly.
