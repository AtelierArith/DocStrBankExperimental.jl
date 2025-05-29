```
Data(), Facet()
```

Data/Facet要素を作成します。 [Vega docs](https://vega.github.io/vega/docs/data/)

引数はデータ構造を説明する名前付き引数です。Tablesインターフェースに準拠するすべてのJuliaオブジェクトを値として使用できます。

# 例

```julia
using DataFrames
N = 100
tb = DataFrame(x=randn(N), y=randn(N), a=rand("ABC", N))

mydata = Data(values=tb)
```
