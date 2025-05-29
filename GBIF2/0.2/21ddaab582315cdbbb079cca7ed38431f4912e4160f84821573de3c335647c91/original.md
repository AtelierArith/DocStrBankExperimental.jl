```
species(key; kw...)
species(key, resulttype; kw...)
```

Query the GBIF `species` api, returning a single `Species`.

  * `key`: a species key, or `Species` object from another search that a key can be   obtained from.
  * `resulttype`: set this so that instead of a `Species`, `species` will return an   object in `(:verbatim, :name, :parents, :children, :related, :synonyms, :combinations, :descriptions, :distributions, :media, :references, :speciesProfiles, :vernacularNames, :typeSpecimens)`. The return value will be a raw JSON3.Object`,   but its`propertynames` can be checked and used to access data.

# Example

Here we find a species with `species_search`, and then obtain the complete record with `species`.

```julia
julia> using GBIF2
julia> tbl = species_search("Falco punctatus")
20-element GBIF2.Table{GBIF2.Species, JSON3.Array{JSON3.Object, Vector{UInt8}, SubArray{
UInt64, 1, Vector{UInt64}, Tuple{UnitRange{Int64}}, true}}}
┌──────────┬──────────┬───────────────┬───────────────┬────────────┬─────────┬──────────
│  kingdom │   phylum │         class │         order │     family │   genus │         ⋯
│  String? │  String? │       String? │       String? │    String? │ String? │         ⋯
├──────────┼──────────┼───────────────┼───────────────┼────────────┼─────────┼──────────
│ Animalia │  missing │          Aves │ Falconiformes │ Falconidae │ missing │ Falco p ⋯
│ Animalia │  missing │          Aves │       missing │ Falconidae │   Falco │ Falco p ⋯
│  missing │  missing │          Aves │ Falconiformes │ Falconidae │   Falco │ Falco p ⋯
│  missing │ Chordata │       missing │       missing │ Falconidae │   Falco │ Falco p ⋯
│ Animalia │ Chordata │          Aves │ Falconiformes │ Falconidae │   Falco │ Falco p ⋯
│ Animalia │ Chordata │          Aves │ Falconiformes │ Falconidae │   Falco │ Falco p ⋯
│  Metazoa │ Chordata │          Aves │ Falconiformes │ Falconidae │   Falco │ Falco p ⋯
│ Animalia │  missing │       missing │ Falconiformes │ Falconidae │ missing │ Falco p ⋯
│  Metazoa │ Chordata │          Aves │ Falconiformes │ Falconidae │   Falco │ Falco p ⋯
│    ⋮     │    ⋮     │       ⋮       │       ⋮       │     ⋮      │    ⋮    │         ⋱
└──────────┴──────────┴───────────────┴───────────────┴────────────┴─────────┴──────────
                                                           35 columns and 11 rows omitted

```

And retrieve all the fields for one of the matches.

```julia
julia> species(tbl[6])
GBIF2.Species({
                   "key": 102091853,
                "nubKey": 2481005,
               "nameKey": 4400647,
               "taxonID": "175650",
               "kingdom": "Animalia",
                "phylum": "Chordata",
                 "order": "Falconiformes",
                "family": "Falconidae",
                 "genus": "Falco",
               "species": "Falco punctatus",
            "kingdomKey": 101683523,
             "phylumKey": 102017110,
              "classKey": 102085317,
              "orderKey": 102091762,
             "familyKey": 102091763,
              "genusKey": 102091765,
            "speciesKey": 102091853,
            "datasetKey": "9ca92552-f23a-41a8-a140-01abaa31c931",
             "parentKey": 102091765,
                "parent": "Falco",
        "scientificName": "Falco punctatus Temminck, 1821",
         "canonicalName": "Falco punctatus",
        "vernacularName": "Mauritius Kestrel",
            "authorship": "Temminck, 1821",
              "nameType": "SCIENTIFIC",
                  "rank": "SPECIES",
                "origin": "SOURCE",
       "taxonomicStatus": "ACCEPTED",
   "nomenclaturalStatus": [],
        "numDescendants": 0,
           "lastCrawled": "2022-10-10T18:15:33.989+00:00",
       "lastInterpreted": "2022-10-10T19:16:16.841+00:00",
                "issues": [
                            "SCIENTIFIC_NAME_ASSEMBLED"
                          ],
               "synonym": false,
                 "class": "Aves"
})
```

## Keyword arguments

  * `language`: can be specified for a single argument or with second argument in   `(:parents, :children, :related, :synonyms)`.
  * `datasetKey`: can be specified, with a second argument `:related`.
