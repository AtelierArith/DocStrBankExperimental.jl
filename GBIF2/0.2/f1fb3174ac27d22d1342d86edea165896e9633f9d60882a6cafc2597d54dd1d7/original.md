```
occurrence_request(sp::Species; kw...)
occurrence_request(; kw...)
```

Request an occurrence download, returning a token that will later provide a download url. You can call `occurrence_download(token)` when it is ready. Prior to that, you will get 404 errors.

# Example

Here we request to dowload all of the occurrences of the Common Myna, *Acridotheres tristis*.

```
julia> sp = species_match("Acridotheres tristis");

julia> occurrence_count(sp)
1936341
julia> token = occurrence_request(sp, username="my_gbif_username")
```

This will prompt for your password, and either throw an error or return a value for the `token` to use later in `occurrence_download`.

If you forgot to store the token and your session is still open, you can simply use `occurrence_download()` to download the most recent request.

# Keywords

  * `username`: String username for a gbif.org account
  * `password`: String password for a gbif.org account. The password   will be entered in the REPL if this keyword is not used.
  * `type`: choose from an `:and` or `:or` query.

Allowed query keywords are: `(:datasetKey, :year, :month, :decimalLatitude, :decimalLongitude, :elevation, :depth, :institutionCode, :collectionCode, :catalogNumber, :scientificName, :occurrenceID, :establishmentMeans, :degreeOfEstablishment, :pathway, :eventDate, :modified, :lastInterpreted, :basisOfRecord, :countryCode, :continent, :publishingCountry, :recordedBy, :identifiedBy, :recordNumber, :typeStatus, :hasCoordinate, :hasGeospatialIssues, :mediaType, :issue, :kingdomKey, :phylumKey, :classKey, :orderKey, :familyKey, :genusKey, :subgenusKey, :speciesKey, :acceptedTaxonKey, :taxonomicStatus, :repatriated, :organismID, :locality, :coordinateUncertaintyInMeters, :stateProvince, :waterBody, :level0Gid, :level1Gid, :level2Gid, :level3Gid, :protocol, :license, :publishingOrgKey, :hostingOrganizationKey, :crawlId, :installationKey, :networkKey, :eventID, :parentEventID, :samplingProtocol, :projectId, :programmeAcronym, :verbatimScientificName, :taxonID, :sampleSizeUnit, :sampleSizeValue, :organismQuantity, :organismQuantityType, :relativeOrganismQuantity, :collectionKey, :institutionKey, :recordedByID, :identifiedByID, :occurrenceStatus, :lifeStage, :isInCluster, :dwcaExtension, :iucnRedListCategory, :datasetID, :datasetName, :otherCatalogNumbers, :preparations)`

# Modifiers

Prameter values can modify the kind of match by using a pair: `elevation = :lessThan => 100`, or using julia Fix2 operators like `elevation = >(100)`.

| Pair key             |  Fix2 | Description                                                                      |
|:-------------------- | -----:|:-------------------------------------------------------------------------------- |
| :equals              | ==(x) | equality comparison                                                              |
| :lessThan            |  <(x) | is less than                                                                     |
| :lessThanOrEquals    | <=(x) | is less than or equals                                                           |
| :greaterThan         | =>(x) | is greater than                                                                  |
| :greaterThanOrEquals | >=(x) | greater than or equals                                                           |
| :in                  | in(x) | specify multiple values to be compared                                           |
| :not                 | !=(x) | logical negation                                                                 |
| :and                 |  &(x) | logical AND (conjuction)                                                         |
| :or                  |       | (x)                                                                              |
| :like                |       | search for a pattern, ? matches one character, * matches zero or more characters |

# To pass instead of a value:

|:isNull    | has an empty value    | |:isNotNull | has a non-empty value |
