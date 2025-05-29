```
readncfile(fname,backend::Module=NCDatasets)
```

NetCDFファイルを読み込み、変数/次元を`NCvar`構造体として返し、ファイル属性を`Dict`として返します。大きな変数/次元はメモリに読み込まれません。これは`NCDatasets.jl`または`NetCDF.jl`のいずれかを使用できます。
