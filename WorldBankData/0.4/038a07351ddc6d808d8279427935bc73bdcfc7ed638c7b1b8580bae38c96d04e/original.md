search_wdi(data::String, entry::String, regx::Regex)::DataFrame

Search World Development Indicators for countries or indicators.

https://datacatalog.worldbank.org/dataset/world-development-indicators

**Arguments**

  * `data` : data to search for: "indicators" or "countries"
  * `entry` : entry to lookup for countries: `name`,`region`,`capital`,`iso2c`,`iso3c`,`income`,`lending` for indicators: `name`, `description`, `topics`, `source_database`, `source_organization`
  * `regex` : regular expression to find

# Examples

```julia
search_wdi("countries", "name", r"united"i)
search_wdi("indicators", "description", r"gross national"i)
```
