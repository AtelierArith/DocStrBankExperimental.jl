```
cdo_locations(CDO_token::AbstractString, location::AbstractString)
cdo_locations(CDO_token::AbstractString;
              datasets::Union{AbstractString, AbstractVector{<:AbstractString}} = "",
              locationcategories::Union{AbstractString, AbstractVector{<:AbstractString}} = "",
              datacategories::Union{AbstractString, AbstractVector{<:AbstractString}} = "",
              startdate::Date = Date(1, 1, 1),
              enddate::Date = today())
```

CDOトークンを取得するには: [Webサービストークンをリクエスト](https://www.ncdc.noaa.gov/cdo-web/token)

追加情報は[NCDCの気候データオンライン（CDO）Webサービスv2ドキュメント](https://www.ncdc.noaa.gov/cdo-web/webservices/v2#locations)をご覧ください。
