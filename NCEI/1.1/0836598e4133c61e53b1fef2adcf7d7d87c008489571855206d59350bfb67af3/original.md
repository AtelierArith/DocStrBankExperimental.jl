```
cdo_locationcategories(CDO_token::AbstractString, locationcategory::AbstractString)
cdo_locationcategories(CDO_token::AbstractString;
                       datasets::Union{AbstractString, AbstractVector{<:AbstractString}} = "",
                       startdate::Date = Date(1, 1, 1),
                       enddate::Date = today())
```

For obtaining a CDO_token: [Request Web Services Token](https://www.ncdc.noaa.gov/cdo-web/token)

For additional information visit the [NCDC's Climate Data Online (CDO) Web Services v2 Documentation](https://www.ncdc.noaa.gov/cdo-web/webservices/v2#locationCategories)
