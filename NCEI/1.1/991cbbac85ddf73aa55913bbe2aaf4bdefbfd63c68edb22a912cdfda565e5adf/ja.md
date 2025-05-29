```
cdo_stations(CDO_token::AbstractString, station::AbstractString)
cdo_stations(CDO_token::AbstractString;
             datasets::Union{AbstractString, AbstractVector{<:AbstractString}} = "",
             locations::Union{AbstractString, AbstractVector{<:AbstractString}} = "",
             datacategories::Union{AbstractString, AbstractVector{<:AbstractString}} = "",
             datatypes::Union{AbstractString, AbstractVector{<:AbstractString}} = "",
             extent::Union{AbstractVector{<:AbstractFloat}} = Vector{Float64}(),
             startdate::Date = Date(1, 1, 1),
             enddate::Date = today())
```

CDOトークンを取得するには: [Webサービストークンをリクエスト](https://www.ncdc.noaa.gov/cdo-web/token)

詳細情報は[NCDCの気候データオンライン（CDO）Webサービスv2ドキュメント](https://www.ncdc.noaa.gov/cdo-web/webservices/v2#stations)をご覧ください。
