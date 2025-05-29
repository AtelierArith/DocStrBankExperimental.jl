```
add_datadep(nam::String)
```

スクラッチスペースフォルダーにデータを追加します。`nam` の既知のオプションには "release1"、"release2"、"release3"、"release4"、"release5"、および "OCCA2HR1" が含まれます。

内部的には、これは次のと同じです：

```
using Climatology
add_datadep("IPCC")
```
