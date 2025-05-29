```
variables(pkg::Module)
```

PlantSimEngineを依存関係として持つパッケージ内のすべての変数、その説明および単位のデータフレームを返します（著者によって実装されている場合）。

# 開発者への注意

PlantSimEngineに依存するパッケージの開発者は、「data/variables.csv」にcsvファイルを置く必要があります。そうすれば、このファイルが関数によって返されます。

# 例

PlantBiophysicsパッケージの例を示します：

```julia
#] add PlantBiophysics
using PlantBiophysics
variables(PlantBiophysics)
```
