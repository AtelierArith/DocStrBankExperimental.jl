```
Data(table)
Data(; url, [format], [name])
Data(generator::SymbolOrString; properties...)
```

`data`プロパティを持つ表示可能な仕様の`DataSpec`を作成します。利用可能なコンストラクタは次のとおりです。

  * [Tables.jl interface](https://github.com/JuliaData/Tables.jl)をサポートする`table`を使用する
  * データを読み込むための`url`を使用し、オプションの`format`および`name`プロパティを指定する。 [](https://vega.github.io/vega-lite/docs/data.html#url)
  * 特定の`properties`を持つ`generator`を使用して、利用可能な[Vega-Liteデータジェネレーター](https://vega.github.io/vega-lite/docs/data.html#data-generators)のいずれかを使用する

詳細は[Vega-Liteの](https://vega.github.io/vega-lite/docs/data.html)および[Denebの](https://brucala.github.io/Deneb.jl/dev/data_mark_encoding/#Data)ドキュメントを参照してください。

# 例

```
# テーブル形式
data = (a=[1, 2], b=["potato", "tomato"])
Data(data)

# URLからのデータ
Data(
    url="https://vega.github.io/vega-datasets/data/us-10m.json",
    format=(type=:topojson, feature=:states),
)

# Vega-Liteジェネレーター
Data(:graticule, step=[15, 15])
```
