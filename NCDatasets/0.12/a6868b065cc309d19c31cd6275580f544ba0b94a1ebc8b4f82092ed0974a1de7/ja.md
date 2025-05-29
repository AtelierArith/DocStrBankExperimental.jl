NCDatasetsはNetCDFファイルを読み書きするためのモジュールです。以下はNetCDFファイルを読み込むための最小限の例です。

```julia
using NCDatasets
# open the file and show its metadata (if called in the REPL without ending semicolon)
ds = NCDataset("filename.nc","r")
# load all data of the variable temperature
v = ds["temperature"][:,:]
# load the attribute units
unit = v.attrib["units"]
# close the file
close(ds)
```

詳細情報は https://github.com/Alexander-Barth/NCDatasets.jl で入手できます。
