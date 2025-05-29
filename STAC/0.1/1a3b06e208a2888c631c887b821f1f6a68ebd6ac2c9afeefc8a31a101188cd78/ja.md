```
cats = eachitem(catalog::Catalog)
```

`catalog`内のすべてのアイテムを再帰的に返します。深くネストされたカタログの場合、これには時間がかかることがあります。

```julia
url = "https://raw.githubusercontent.com/sat-utils/sat-stac/master/test/catalog/catalog.json"

cat = STAC.Catalog(url)
for c in eachitem(cat)
    @show id(c)
end
```
