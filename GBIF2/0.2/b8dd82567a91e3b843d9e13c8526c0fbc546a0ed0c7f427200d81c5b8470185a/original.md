```
occurrence_count(species::Species; kw...)
occurrence_count(; kw...)
```

Count the number of occurrences for a taxon.

# Example

```
juila> sp = species_match("Pteropus niger");

juila> occurrence_count(sp)
559
```

# Keywords

  * `taxonKey`: is the most useful key when a `Species` is not passed.

Occurrence counts have a complicated schema of allowed keyword combinations. You can access these from the GBIF api using `GBIF2.occurrence_count_schema()`.
