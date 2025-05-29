```
ECCOdiags_add(nam::String)
```

スクラッチスペースフォルダーにデータを追加します。`nam`の既知のオプションには「release1」、「release2」、「release3」、「release4」、「release5」、および「OCCA2HR1」が含まれます。

内部的には、これは次のと同じです：

```
using Climatology
datadep"ECCO4R1-stdiags"
datadep"ECCO4R2-stdiags"
datadep"ECCO4R3-stdiags"
datadep"ECCO4R4-stdiags"
datadep"ECCO4R5-stdiags"
datadep"OCCA2HR1-stdiags"
```
