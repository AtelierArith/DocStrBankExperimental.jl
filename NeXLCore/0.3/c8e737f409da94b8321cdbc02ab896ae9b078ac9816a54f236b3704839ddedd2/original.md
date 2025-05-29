```
wikidata_minerals()::Dict{String, Material}
```

Mineral data based on a WikiData SPARQL query of minerals. Only those minerals which represented distinct (uniquely defined) compositions are included.  Replicas were removed.

Also includes `:Class`, `:Formula` and `:Description` properties.
