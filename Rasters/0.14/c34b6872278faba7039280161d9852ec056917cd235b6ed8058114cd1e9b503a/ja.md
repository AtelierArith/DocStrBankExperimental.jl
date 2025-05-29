```
convertlookup(dstlookup::Type{<:Lookup}, x)
```

`Projected` と `Mapped` の間で次元ルックアップを変換します。他の次元ルックアップはそのまま通過します。

これは、例えば netcdf ファイルを GeoTiff に保存するために使用されます。
