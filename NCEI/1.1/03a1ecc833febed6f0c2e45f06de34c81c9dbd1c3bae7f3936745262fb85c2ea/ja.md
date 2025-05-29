```
cdo_datacategories(CDO_token::AbstractString, datacategory::AbstractString)
cdo_datacategories(CDO_token::AbstractString;
                   datasets::Union{AbstractString, AbstractVector{<:AbstractString}} = "",
                   locations::Union{AbstractString, AbstractVector{<:AbstractString}} = "",
                   stations::Union{AbstractString, AbstractVector{<:AbstractString}} = "",
                   startdate::Date = Date(1, 1, 1),
                   enddate::Date = today())
```

CDOトークンを取得するには: [Webサービストークンをリクエスト](https://www.ncdc.noaa.gov/cdo-web/token)

追加情報については、[NCDCの気候データオンライン（CDO）Webサービスv2ドキュメント](https://www.ncdc.noaa.gov/cdo-web/webservices/v2#dataCategories)をご覧ください。
