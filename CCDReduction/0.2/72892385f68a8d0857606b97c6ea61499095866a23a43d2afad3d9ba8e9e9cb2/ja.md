```
ccds(collection)
```

データフレーム内のエントリの `CCDData` のジェネレーター。

各 `path` と `hdu` を使用して `collection` を反復処理し、データを [`CCDData`](@ref) にロードします。

# 例

```julia
collection = fitscollection("~/data/tekdata")
for hdu in ccds(collection)
    @assert hdu isa CCDData
end
```
