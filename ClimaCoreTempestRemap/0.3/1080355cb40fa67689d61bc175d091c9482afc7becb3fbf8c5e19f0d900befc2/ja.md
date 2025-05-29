```
overlap_mesh(outfile::AbstractString, meshfile_a::AbstractString, meshfile_b::AbstractString; verbose=false)
```

`meshfile_a` と `meshfile_b` のオーバラップメッシュを作成し、`outfile` に書き込みます。すべてのファイルはExodus形式である必要があります。

`verbose=true` に設定すると、情報が表示されます。

See [Tempest remap: mesh generation](https://github.com/ClimateGlobalChange/tempestremap/#mesh-generation)
