```
cdo_locationcategories(CDO_token::AbstractString, locationcategory::AbstractString)
cdo_locationcategories(CDO_token::AbstractString;
                       datasets::Union{AbstractString, AbstractVector{<:AbstractString}} = "",
                       startdate::Date = Date(1, 1, 1),
                       enddate::Date = today())
```

CDOトークンを取得するには: [Request Web Services Token](https://www.ncdc.noaa.gov/cdo-web/token)

追加情報は[NCDCの気候データオンライン (CDO) Webサービス v2 ドキュメント](https://www.ncdc.noaa.gov/cdo-web/webservices/v2#locationCategories)をご覧ください。
