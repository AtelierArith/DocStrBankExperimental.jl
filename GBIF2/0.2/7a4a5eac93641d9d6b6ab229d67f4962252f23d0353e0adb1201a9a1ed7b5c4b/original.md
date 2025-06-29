```
occurrence_search(species::Species; kw...)
occurrence_search([q]; kw...)
occurrence_search(q, returntype; limit...)
```

Search for occurrences, returning a `Table{Occurrence}` table.

# Example

Here we find a species with `species_match`, and then retrieve all the occurrences with `occurrence_search`.

```julia
julia> 
using GBIF2

julia> 
sp = species_match("Falco punctatus");

julia> 
ocs = occurrence_search(sp; continent=:AFRICA, limit=1000)
[ Info: 522 occurrences found, limit was 1000
522-element GBIF2.Table{GBIF2.Occurrence, Vector{JSON3.Object}}
┌──────────────────┬─────────────────┬────────┬────────┬────────┬────────────
│ decimalLongitude │ decimalLatitude │   year │  month │    day │  kingdom  ⋯
│         Float64? │        Float64? │ Int64? │ Int64? │ Int64? │  String?  ⋯
├──────────────────┼─────────────────┼────────┼────────┼────────┼────────────
│          missing │         missing │   2012 │      8 │     18 │ Animalia  ⋯
│          missing │         missing │   2010 │      1 │     29 │ Animalia  ⋯
│          57.2452 │        -20.2239 │   2009 │     10 │     26 │ Animalia  ⋯
│          57.2452 │        -20.2239 │   2009 │     11 │      5 │ Animalia  ⋯
│          57.2452 │        -20.2239 │   2009 │     11 │      5 │ Animalia  ⋯
│          57.2452 │        -20.2239 │   2009 │     11 │      4 │ Animalia  ⋯
│          57.2452 │        -20.2239 │   2009 │     11 │      5 │ Animalia  ⋯
│          57.2452 │        -20.2239 │   2009 │     11 │      4 │ Animalia  ⋯
│          57.7667 │          -19.85 │   2007 │      6 │     19 │ Animalia  ⋯
│          57.7667 │          -19.85 │   2007 │      6 │     19 │ Animalia  ⋯
│          57.7667 │          -19.85 │   2007 │      6 │     19 │ Animalia  ⋯
│          57.7667 │          -19.85 │   2007 │      6 │     19 │ Animalia  ⋯
│          57.7667 │          -19.85 │   2007 │      6 │     19 │ Animalia  ⋯
│          57.7667 │          -19.85 │   2007 │      6 │     19 │ Animalia  ⋯
│          57.7667 │          -19.85 │   2007 │      6 │     19 │ Animalia  ⋯
│        ⋮         │        ⋮        │   ⋮    │   ⋮    │   ⋮    │    ⋮      ⋱
└──────────────────┴─────────────────┴────────┴────────┴────────┴────────────
                                              78 columns and 507 rows omitted
```

# Arguments

  * `q`: a search query.
  * `species`: if the first value is a species, search keywords will be retrieved from it.
  * `returntype`: modify the returntype, with a `Symbol` from :

      * `:catalogNumber`: Search that returns matching catalog numbers. Table are ordered by relevance.
      * `:collectionCode`: Search that returns matching collection codes. Table are ordered by relevance.
      * `:occurrenceId`: Search that returns matching occurrence identifiers. Table are ordered by relevance.
      * `:recordedBy`: Search that returns matching collector names. Table are ordered by relevance.
      * `:recordNumber`: Search that returns matching record numbers. Table are ordered by relevance.
      * `:institutionCode`: Search that returns matching institution codes. Table are ordered by relevance.

# Keywords

We use parameters exactly as in the [GBIF api](https://www.gbif.org/developer/species).

You can find keyword enum values with the `[GBIF2.enum](@ref)` function.

GBIF range queries work by putting values in a `Tuple`, e.g. `elevation=(10, 100)`.

  * `basisOfRecord`: Basis of record, as defined in our BasisOfRecord enum
  * `catalogNumber`: An identifier of any form assigned by the source within a physical collection or digital dataset for the record which may not be unique, but should be fairly unique in combination with the institution and collection code.
  * `classKey`: Class classification key.
  * `collectionCode`: An identifier of any form assigned by the source to identify the physical collection or digital dataset uniquely within the context of an institution.
  * `continent`: Continent, as defined in our Continent enum
  * `coordinateUncertaintyInMeters`: The horizontal distance (in meters) from the given decimalLatitude and decimalLongitude describing the smallest circle containing the whole of the Location. Supports range queries.
  * `country`: The 2-letter country code (as per ISO-3166-1) of the country in which the occurrence was recorded.
  * `crawlId`: Crawl attempt that harvested this record.
  * `datasetId`: The ID of the dataset.
  * `datasetKey`: The occurrence dataset key (a uuid).
  * `datasetName`: The name of the dataset.
  * `decimalLatitude`: Latitude in decimals between -90 and 90 based on WGS 84. Supports range queries.
  * `decimalLongitude`: Longitude in decimals between -180 and 180 based on WGS 84. Supports range queries.
  * `depth`: Depth in meters relative to altitude. For example 10 meters below a lake surface with given altitude. Supports range queries.
  * `elevation`: Elevation (altitude) in meters above sea level. Supports range queries.
  * `establishmentMeans`: EstablishmentMeans, as defined in our EstablishmentMeans enum
  * `eventDate`: Occurrence date in ISO 8601 format: `yyyy`, `yyyy-MM`, `yyyy-MM-dd`, or `MM-dd`. Supports range queries.
  * `eventId`: An identifier for the information associated with a sampling event.
  * `facet`: A facet name used to retrieve the most frequent values for a field. Facets are allowed for all the parameters except for: eventDate, geometry, lastInterpreted, locality, organismId, stateProvince, waterBody. This parameter may by repeated to request multiple facets, as in this example /occurrence/search?facet=datasetKey&facet=basisOfRecord&limit=0
  * `facetMincount`: Used in combination with the facet parameter. Set facetMincountN to exclude facets with a count less than N, e.g. /search?facet=type&limit=0&facetMincount=10000 only shows the type value 'OCCURRENCE' because 'CHECKLIST' and 'METADATA' have counts less than 10000.
  * `facetMultiselect`: Used in combination with the facet parameter. Set facetMultiselect=true to still return counts for values that are not currently filtered, e.g. /search?facet=type&limit=0&type=CHECKLIST&facetMultiselect=true still shows type values 'OCCURRENCE' and 'METADATA' even though type is being filtered by type=CHECKLIST
  * `facetOffset`:
  * `facetLimit`: Facet parameters allow paging requests using the parameters facetOffset and facetLimit as this example /occurrence/search?facet=datasetKey&datasetKey.facetLimit=5&datasetKey.facetOffset=10&limit=0
  * `familyKey`: Family classification key.
  * `format`: Export format, accepts TSV(default) and CSV
  * `fromDate`: Start partial date of a date range, accepts the format `yyyy-MM`, for example: `2015-11`
  * `gadmGid`: A GADM geographic identifier at any level, for example AGO, AGO.1*1, AGO.1.1*1 or AGO.1.1.1_1
  * `gadmLevel`: A GADM region level, valid values range from 0 to 3
  * `gadmLevel0Gid`: A GADM geographic identifier at the zero level, for example AGO
  * `gadmLevel1Gid`: A GADM geographic identifier at the first level, for example AGO.1_1
  * `gadmLevel2Gid`: A GADM geographic identifier at the second level, for example AFG.1.1_1
  * `gadmLevel3Gid`: A GADM geographic identifier at the third level, for example AFG.1.1.1_1
  * `genusKey`: Genus classification key.
  * `geoDistance`: Filters to match occurrence records with coordinate values within a specified distance of a coordinate, it supports units: in (inch), yd (yards), ft (feet), km (kilometers), mmi (nautical miles), mm (millimeters), cm centimeters, mi (miles), m (meters), for example /occurrence/search?geoDistance=90,100,5km
  * `geometry`: Searches for occurrences inside a polygon described in Well Known Text (WKT) format. Only POINT, LINESTRING, LINEARRING, POLYGON and MULTIPOLYGON are accepted WKT types. For example, a shape written as POLYGON ((30.1 10.1, 40 40, 20 40, 10 20, 30.1 10.1)) would be queried as is, i.e. /occurrence/search?geometry=POLYGON((30.1 10.1, 40 40, 20 40, 10 20, 30.1 10.1)). Polygons must have anticlockwise ordering of points, or will give unpredictable results. (A clockwise polygon represents the opposite area: the Earth's surface with a 'hole' in it. Such queries are not supported.)
  * `hasCoordinate`: Limits searches to occurrence records which contain a value in both latitude and longitude (i.e. `hasCoordinate=true` limits to occurrence records with coordinate values and `hasCoordinate=false limits to occurrence records without coordinate values).
  * `hasGeospatialIssue`: Includes/excludes occurrence records which contain spatial issues (as determined in our record interpretation), i.e. hasGeospatialIssue=true returns only those records with spatial issues while hasGeospatialIssue=false includes only records without spatial issues. The absence of this parameter returns any record with or without spatial issues.
  * `hl`: Set hl=true to highlight terms matching the query when in fulltext search fields. The highlight will be an emphasis tag of class 'gbifH1' e.g. /search?q=plant&hl=true. Fulltext search fields include: title, keyword, country, publishing country, publishing organization title, hosting organization title, and description. One additional full text field is searched which includes information from metadata documents, but the text of this field is not returned in the response.
  * `identifiedBy`: The person who provided the taxonomic identification of the occurrence.
  * `identifiedByID`: Identifier (e.g. ORCID) for the person who provided the taxonomic identification of the occurrence.
  * `institutionCode`: An identifier of any form assigned by the source to identify the institution the record belongs to. Not guaranteed to be unique.
  * `issue`: A specific interpretation issue as defined in our OccurrenceIssue enum
  * `kingdomKey`: Kingdom classification key.
  * `lastInterpreted`: This date the record was last modified in GBIF, in ISO 8601 format: `yyyy`, `yyyy-MM`, `yyyy-MM-dd`, or `MM-dd`. Supports range queries. Note that this is the date the record was last changed in GBIF, not necessarily the date the record was first/last changed by the publisher. Data is re-interpreted when we change the taxonomic backbone, geographic data sources, or interpretation processes.
  * `license`: The type license applied to the dataset or record.
  * `limit`: The maximum number of results to return. This can't be greater than 300, any value greater is set to 300.
  * `locality`: The specific description of the place.
  * `mediaType`: The kind of multimedia associated with an occurrence as defined in our MediaType enum
  * `modified`: The most recent date-time on which the resource was changed, according to the publisher
  * `month`: The month of the year, starting with 1 for January. Supports range queries.
  * `networkKey`: The GBIF Network to which the occurrence belongs.
  * `occurrenceId`: A single globally unique identifier for the occurrence record as provided by the publisher.
  * `occurrenceStatus`: Either 'ABSENT' or 'PRESENT'; the presence or absence of the occurrence.
  * `offset`: Offset to start results from
  * `orderKey`: Order classification key.
  * `organismId`: An identifier for the Organism instance (as opposed to a particular digital record of the Organism). May be a globally unique identifier or an identifier specific to the data set.
  * `organismQuantity`: A number or enumeration value for the quantity of organisms.
  * `organismQuantityType`: The type of quantification system used for the quantity of organisms.
  * `otherCatalogNumbers`: Previous or alternate fully qualified catalog numbers.
  * `phylumKey`: Phylum classification key.
  * `preparations`: Preparation or preservation method for a specimen.
  * `programme`: A group of activities, often associated with a specific funding stream, such as the GBIF BID programme.
  * `projectId`: The identifier for a project, which is often assigned by a funded programme.
  * `protocol`: Protocol or mechanism used to provide the occurrence record.
  * `publishingCountry`: The 2-letter country code (as per ISO-3166-1) of the owining organization's country.
  * `publishingOrg`: The publishing organization key (a uuid).
  * `publishingOrgKey`: The publishing organization key (a uuid).
  * `q`: Simple search parameter. The value for this parameter can be a simple word or a phrase.
  * `recordedBy`: The person who recorded the occurrence.
  * `recordedByID`: Identifier (e.g. ORCID) for the person who recorded the occurrence.
  * `recordNumber`: An identifier given to the record at the time it was recorded in the field.
  * `relativeOrganismQuantity`: The relative measurement of the quantity of the organism (i.e. without absolute units).
  * `repatriated`: Searches for records whose publishing country is different to the country where the record was recorded in.
  * `sampleSizeUnit`: The unit of measurement of the size (time duration, length, area, or volume) of a sample in a sampling event.
  * `sampleSizeValue`: A numeric value for a measurement of the size (time duration, length, area, or volume) of a sample in a sampling event.
  * `samplingProtocol`: The name of, reference to, or description of the method or protocol used during a sampling event
  * `scientificName`: A scientific name from the GBIF backbone. All included and synonym taxa are included in the search. Under the hood a call to the species match service is done first to retrieve a taxonKey. Only unique scientific names will return results, homonyms (many monomials) return nothing! Consider to use the taxonKey parameter instead and the species match service directly
  * `speciesKey`: Species classification key.
  * `stateProvince`: he name of the next smaller administrative region than country (state, province, canton, department, region, etc.) in which the Location occurs.
  * `subgenusKey`: Subgenus classification key.
  * `taxonKey`: A taxon key from the GBIF backbone. All included and synonym taxa are included in the search, so a search for aves with taxonKey=212 (i.e. `coordinate_search(; taxonKey=212)`) will match all birds, no matter which species.
  * `toDate`: End partial date of a date range, accepts the format `yyyy-MM`, for example: `2019-12`
  * `typeStatus`: Nomenclatural type (type status, typified scientific name, publication) applied to the subject.
  * `userCountry`: Country country of the user who made the requested
  * `verbatimScientificName`: The scientific name provided to GBIF by the data publisher, before interpretation and processing by GBIF.
  * `verbatimTaxonId`: The taxon identifier provided to GBIF by the data publisher.
  * `waterBody`: The name of the water body in which the Locations occurs.
  * `year`: The 4 digit year. A year of `98` will be interpreted as AD 98. Supports range queries.
