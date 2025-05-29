search_wdi(data::String, entry::String, regx::Regex)::DataFrame

世界開発指標を国または指標で検索します。

https://datacatalog.worldbank.org/dataset/world-development-indicators

**引数**

  * `data` : 検索するデータ: "indicators" または "countries"
  * `entry` : 国を検索するためのエントリ: `name`,`region`,`capital`,`iso2c`,`iso3c`,`income`,`lending` 指標の場合: `name`, `description`, `topics`, `source_database`, `source_organization`
  * `regex` : 検索する正規表現

# 例

```julia
search_wdi("countries", "name", r"united"i)
search_wdi("indicators", "description", r"gross national"i)
```
