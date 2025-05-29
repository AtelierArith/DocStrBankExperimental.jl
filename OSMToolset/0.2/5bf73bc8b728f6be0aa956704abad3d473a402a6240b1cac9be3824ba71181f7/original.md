```
attractiveness(sindex::AttractivenessSpatIndex{T}, lattitude::Number, longitude::Number; aggregator::Function=sum, calculate_attractiveness::Function=calculate_attractiveness,  distance::Function=OpenStreetMapX.distance, explain::Bool=false)  where T <: AbstractMetaPOI
```

Returns the multidimensional attractiveness measure for the given spatial index `sindex` and `lattitude` and `longitude`. The `aggregator` function will be used to aggregate the attractiveness values. The aggreagation is required as more than one point of interest can be found within the attractiveness range. The function `calculate_attractiveness(a::T, poidistance::Number)` will be used to calculate the attractiveness on the base of metadata and distance. The distance function `distance(a::ENU, b::ENU)` is used to calculate the distance between point pairs.

If `explain` is set to true the result will additionally contain details about POIs used to calculate the attractiveness.
