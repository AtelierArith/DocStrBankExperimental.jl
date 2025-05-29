```
cats = eachcatalog(catalog::Catalog)
```

Returns resursively all subcatalogs in `catalog`. This can take a long time for deeply nested catalogs.

```julia
url = "https://raw.githubusercontent.com/sat-utils/sat-stac/master/test/catalog/catalog.json"

cat = STAC.Catalog(url)
for c in eachcatalog(cat)
    @show id(c)
end
```
