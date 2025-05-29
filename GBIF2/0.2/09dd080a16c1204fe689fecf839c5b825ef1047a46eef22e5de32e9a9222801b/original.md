```
species_match(; kw...)
```

Query the GBIF `species/match` api, returning the single closest `Species` using fuzzy search.

The results are not particularly detailed, this can be improved by calling  `species(res)` on the result of `species_match` to query for the full dataset.

# Example

```julia
using GBIF2
sp = species_match("Lalage newtoni")

# output
GBIF2.Species({
           "usageKey": 8385394,
   "acceptedUsageKey": 2486791,
     "scientificName": "Lalage newtoni (Pollen, 1866)",
      "canonicalName": "Lalage newtoni",
               "rank": "SPECIES",
             "status": "SYNONYM",
         "confidence": 98,
          "matchType": "EXACT",
            "kingdom": "Animalia",
             "phylum": "Chordata",
              "order": "Passeriformes",
             "family": "Campephagidae",
              "genus": "Coracina",
            "species": "Coracina newtoni",
         "kingdomKey": 1,
          "phylumKey": 44,
           "classKey": 212,
           "orderKey": 729,
          "familyKey": 9284,
           "genusKey": 2482359,
         "speciesKey": 2486791,
            "synonym": true,
              "class": "Aves"
})
```

## Keywords

We use keywords exactly as in the [GBIF api](https://www.gbif.org/developer/species).

You can find keyword enum values with the `[GBIF2.enum](@ref)` function.

  * `rank`: Filters by taxonomic rank as given in our Rank enum
  * `name`: Name of the species
  * `strict`: If `true` it (fuzzy) matches only the given name, but never a taxon in the upper classification
  * `verbose`: If `true` it shows alternative matches which were considered but then rejected
  * `kingdom`: Optional kingdom classification accepting a canonical name.
  * `phylum`: Optional phylum classification accepting a canonical name.
  * `class`: Optional class classification accepting a canonical name.
  * `order`: Optional order classification accepting a canonical name.
  * `family`: Optional family classification accepting a canonical name.
  * `genus`: Optional genus classification accepting a canonical name.
