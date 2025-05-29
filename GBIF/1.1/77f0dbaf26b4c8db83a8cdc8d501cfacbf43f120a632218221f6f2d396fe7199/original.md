```
occurrences(query::Pair...)
```

This function will return the latest occurrences matching the queries – usually 20, but this is entirely determined by the server default page size. The query parameters must be given as pairs, and are optional. Omitting the query will return the latest recorded occurrences for all taxa.

The arguments accepted as queries are documented on the [GBIF API](https://www.gbif.org/developer/occurrence) website.

**Note that** this function will return even observations where the "occurrenceStatus" is "ABSENT"; therefore, for the majority of uses, your query will *at least* contain `"occurrenceStatus" => "PRESENT"`.
