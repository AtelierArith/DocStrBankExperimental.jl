```
search(base_search::Search, property::Union{<:PropertySearchFields, Nothing}=nothing; token::Union{Dict{String, Any}, Nothing}=nothing)
```

Perform a search in the Idealista Search API

This method uses keyword arguments corresponding to valid search fields of the Idealista Search API

# Keyword Argyments

  * `token_d`: Dict containing the API response for a token request
  * `kwargs`: search fields of the Idealista Search API

# Examples

```julia
julia>search(country="es", center="40.430,-3.702", propertyType="homes", distance=15000, operation="sale", bedrooms="1,2,3,4", swimmingPool=true)
[ Info: Getting new access token
Dict{String, Any} with 12 entries:
  "hiddenResults"      => false
  "itemsPerPage"       => 20
  "upperRangePosition" => 20
  "totalPages"         => 206
  "paginable"          => true
  "summary"            => Any["Comprar", "Viviendas", "barrio Trafalgar, Madrid", "Todos los…
  "total"              => 4118
  "lowerRangePosition" => 0
  "alertName"          => "Viviendas en barrio Trafalgar, Madrid"
  "elementList"        => Any[Dict{String, Any}("rooms"=>6, "propertyCode"=>"98324891", "num…
  "numPaginations"     => 0
  "actualPage"         => 1

```
