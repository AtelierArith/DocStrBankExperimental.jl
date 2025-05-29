```
loadmultispec(path::AbstractString, basefn::AbstractString; indexes=0:3, fnmapper::String = "{1}[{2}].msa")
```

`basefn` と `fnmapper` を使用して、どのスペクトルをロードするかを決定しながら、複数のスペクトルをロードします。スペクトルは、すべて同時に収集されたものであるため、同じ `:RealTime`、`:BeamEnergy` および `:LiveTime` を持つという意味で関連している必要があります。
