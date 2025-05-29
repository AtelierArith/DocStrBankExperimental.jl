```
    aggregate_data_legacy(; hData, hParameters, hSets, comMap, regMap, endMap)
```

Aggregates data, parameters and sets based on the provided mapping vectors while incorporating an error in aggregation found in GTAPAgg2 or FlexAgg, where three parameters (i.e., ESUBM, ESUBD and ESUBV) are aggregated globally even though they are defined as region-specific

### Args:

  * `hData`: a dictionary of GTAP data (arrays) with the names as found in HAR files
  * `hParameters`: a dictionary of GTAP parameters (arrays) with the names as found in HAR files
  * `hSets`: a dictionary of GTAP sets (vectors of strings) with the names as found in HAR files
  * `comMap`: a mapping vector (NamedVector) which provides for each element in set `comm` the desired aggregate name
  * `regMap`: a mapping vector (NamedVector) which provides for each element in set `reg` the desired aggregate name
  * `endMap`: a mapping vector (NamedVector) which provides for each element in set `endw` the desired aggregate name

### Retruns:

A named tuple with elements hData, hParameters, hSets containing the aggregated data

### Example:

`julia (; hData, hParameters, hSets) = aggregate_data_legacy(hData=data, hParameters=parameters, hSets=sets, comMap=comMap, regMap=regMap, endMap=endMap)`
