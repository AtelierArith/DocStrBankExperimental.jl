```
search(base_search::Search, property::Union{<:PropertySearchFields, Nothing}=nothing; token::Union{Dict{String, Any}, Nothing}=nothing)
```

Idealista Search APIで検索を実行します

このメソッドは、Searchおよびpropertyタイプのインスタンスを引数として使用します

# 引数

  * `base_search`: Searchオブジェクト
  * `property`: 住宅、店舗、ガレージ、寝室、またはオフィスオブジェクト

# キーワード引数

  * `token_d`: トークンリクエストのAPIレスポンスを含む辞書

# 例

```julia
julia>search(Search(country="es", center="40.430,-3.702", propertyType="homes", distance=15000, operation="sale"), Homes(bedrooms="1,2,3,4", swimmingPool=true))
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
