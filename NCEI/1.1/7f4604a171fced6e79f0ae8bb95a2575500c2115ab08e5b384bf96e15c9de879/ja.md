```
cdo_data(CDO_token::AbstractString, dataset::AbstractString, startdate::Date, enddate::Date;
         datatypes::Union{AbstractString, AbstractVector{<:AbstractString}} = "",
         locations::Union{AbstractString, AbstractVector{<:AbstractString}} = "",
         stations::Union{AbstractString, AbstractVector{<:AbstractString}} = "",
         metric::Bool = true)
```

CDOトークンを取得するには: [Request Web Services Token](https://www.ncdc.noaa.gov/cdo-web/token)

追加情報は、[NCDC's Climate Data Online (CDO) Web Services v2 Documentation](https://www.ncdc.noaa.gov/cdo-web/webservices/v2#data)をご覧ください。
