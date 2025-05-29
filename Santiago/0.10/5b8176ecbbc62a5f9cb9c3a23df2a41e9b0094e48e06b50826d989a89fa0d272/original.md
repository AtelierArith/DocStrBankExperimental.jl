# Calculate the technology appropriateness score (TAS) for each technology

```
appropriateness(technology_file::AbstractString, case_file::AbstractString)
```

## Parameters

  * `technology_file`: name of a json file with technologie definitions
  * `case_file`: name of a json file with case definition

## Values

Two dictionaries. The first one return the TAS for each technology, the second one contains the scores separately for each attribute.
