```
species_search([q]; kw...)
```

Query the GBIF `species/search` api, returning many results in a [`GBIF2.Table`](@ref).

# Example

```julia
using GBIF2
sp = species_search("Psittacula eques")

# output
20-element GBIF2.Table{GBIF2.Species, JSON3.Array{JSON3.Object, Vector{UInt8}, SubArray{UInt64, 1,
Vector{UInt64}, Tuple{UnitRange{Int64}}, true}}}
┌──────────┬──────────┬────────────────┬────────────────┬───────────────┬──────────────┬──
│  kingdom │   phylum │          class │          order │        family │        genus │ ⋯
│  String? │  String? │        String? │        String? │       String? │      String? │ ⋯
├──────────┼──────────┼────────────────┼────────────────┼───────────────┼──────────────┼──
│ Animalia │ Chordata │           Aves │ Psittaciformes │ Psittaculidae │   Psittacula │ ⋯
│ Animalia │  missing │           Aves │ Psittaciformes │ Psittaculidae │      missing │ ⋯
│  Metazoa │ Chordata │           Aves │ Psittaciformes │   Psittacidae │   Psittacula │ ⋯
│ Animalia │  missing │           Aves │ Psittaciformes │ Psittaculidae │      missing │ ⋯
│ Animalia │  missing │           Aves │ Psittaciformes │ Psittaculidae │      missing │ ⋯
│ Animalia │  missing │        missing │ Psittaciformes │ Psittaculidae │      missing │ ⋯
│  Metazoa │ Chordata │           Aves │ Psittaciformes │   Psittacidae │   Psittacula │ ⋯
│  missing │  missing │        missing │        missing │       missing │   Psittacula │ ⋯
│ Animalia │ Chordata │           Aves │ Psittaciformes │ Psittaculidae │   Psittacula │ ⋯
│ Animalia │  missing │           Aves │        missing │   Psittacidae │   Psittacula │ ⋯
│  Metazoa │ Chordata │           Aves │ Psittaciformes │   Psittacidae │   Psittacula │ ⋯
│ Animalia │ Chordata │           Aves │ Psittaciformes │ Psittaculidae │   Psittacula │ ⋯
│ ANIMALIA │ CHORDATA │ PSITTACIFORMES │           AVES │   PSITTACIDAE │ Alexandrinus │ ⋯
│  Metazoa │ Chordata │           Aves │ Psittaciformes │   Psittacidae │   Psittacula │ ⋯
│ Animalia │ Chordata │           Aves │ Psittaciformes │   Psittacidae │   Psittacula │ ⋯
│ Animalia │  missing │           Aves │ Psittaciformes │ Psittaculidae │   Psittacula │ ⋯
│    ⋮     │    ⋮     │       ⋮        │       ⋮        │       ⋮       │      ⋮       │ ⋱
└──────────┴──────────┴────────────────┴────────────────┴───────────────┴──────────────┴──
                                                              37 columns and 4 rows omitted
```

## Keyword arguments

We use keywords exactly as in the [GBIF api](https://www.gbif.org/developer/species).

  * `class`: Optional class classification accepting a canonical name.
  * `datasetKey`: Filters by the checklist dataset key (a uuid)
  * `facet`: A list of facet names used to retrieve the 100 most frequent values for a field. Allowed facets are `:datasetKey`, `:higherTaxonKey`, `:rank`, `:status`, `:nomenclaturalStatus`, `isExtinct`, `:habitat`, `:threat` and `:nameType`.
  * `facetMincount`: Used in combination with the facet parameter. Set facetMincount=N to exclude facets with a count less than N, e.g. `facet=type, limit=>0, facetMincount=>10000` only shows the type value `OCCURRENCE` because `:CHECKLIST` and `:METADATA` have counts less than 10000.
  * `facetMultiselect`: Used in combination with the facet parameter. Set `facetMultiselect=true` to still return counts for values that are not currently filtered, e.g. `facet=type, limit=>0, type=>CHECKLIST, facetMultiselect=>true` still shows type values `OCCURRENCE` and `METADATA` even though type is being filtered by `type=:CHECKLIST`
  * `family`: Optional family classification accepting a canonical name.
  * `genus`: Optional genus classification accepting a canonical name.
  * `habitat`: Filters by the habitat. Currently only 3 major biomes are accepted in our Habitat enum
  * `highertaxonKey`: Filters by any of the higher Linnean rank keys. Note this is within the respective checklist and not searching nub keys across all checklists.
  * `hl`: Set `hl=true` to highlight terms matching the query when in fulltext search fields. The highlight will be an emphasis tag of class 'gbifH1' e.g. `q="plant", hl=>true`. Fulltext search fields include title, keyword, country, publishing country, publishing organization title, hosting organization title, and description. One additional full text field is searched which includes information from metadata documents, but the text of this field is not returned in the response
  * `isExtinct`: Filters by extinction status (a boolean, e.g. isExtinct=>true)
  * `issue`: A specific indexing issue as defined in our NameUsageIssue enum
  * `kingdom`: Optional kingdom classification accepting a canonical name.
  * `language`: Language for vernacular names, given as an ISO 639-1 two-letter code from our
  * `nameType`: Filters by the name type as given in our NameType enum
  * `nomenclaturalStatus`: Not yet implemented, but will eventually allow for filtering by a nomenclatural status enum
  * `order`: Optional order classification accepting a canonical name.
  * `phylum`: Optional phylum classification accepting a canonical name.
  * `q`: Simple full text search parameter. The value for this parameter can be a simple word or a phrase. Wildcards are not supported
  * `rank`: Filters by taxonomic rank as given in our Rank enum
  * `sourceId`: Filters by the source identifier
  * `status`: Filters by the taxonomic status as given in our TaxonomicStatus enum
  * `strict`: If `true` it (fuzzy) matches only the given name, but never a taxon in the upper classification
  * `threat`: Filters by the taxonomic threat status as given in our ThreatStatus enum
  * `verbose`: If `true` it shows alternative matches which were considered but then rejected
  * `offset`: Offset to start results from
  * `limit`: The maximum number of results to return. This can't be greater than 300, any value greater is set to 300.
