```
ClimArray(A::Array, dims::Tuple; name = "", attrib = nothing)
```

`ClimArray`は、次元情報、名前、および一般的な属性を保持する`attrib`フィールド（通常は辞書）をバンドルした数値配列データを含む構造体です。`ClimArray`はCFVariableのメモリ内表現と考えることができます。

現在、`ClimArray`はDimensionalData.jlの`DimArray`を使用しており、`ClimArray`の基本的な処理はすべて`DimensionalData`によって提供されています（以下を参照）。

`ClimArray`は、標準の配列データ`A`と次元のタプル`dims`を渡すことによって作成されます。`.nc`ファイルから自動的に`ClimArray`を作成するには、[`ncread`](@ref)を参照してください。`ClimArray`またはその任意の次元の生の数値を取得するには、関数[`gnv`](@ref)を使用します。

## 例

```julia
using ClimateBase, Dates
Time = ClimateBase.Ti # 時間次元のより直感的な名前
lats = -90:5:90
lons = 0:10:359
t = Date(2000, 3, 15):Month(1):Date(2020, 3, 15)
# 次元情報:
dimensions = (Lon(lons), Lat(lats), Time(t))
data = rand(36, 37, 241) # 数値データ
A = ClimArray(data, dimensions)
```
