```
slice(var::OutputVar, kwargs...)
```

キーワード引数で定義された次元に沿ってスライスすることによって新しいOutputVarを返します。

時間次元が選択され、`start_date`が`var`の属性の中にある場合、`Dates.DateTime`を直接渡すことが可能で、`slice`は自動的にそれを対応する時間に変換します。

# 例

```julia
slice(var, lat = 30, lon = 20, time = 100)
```

`var`に`start_date`が属性の中にある場合。

```julia
import Dates
slice(var, lat = 30, lon = 20, time = Dates.DateTime(2020, 12, 21))
```

!!! compat "Datesおよび一般化された次元名のサポート"
    `DateTime`を使用して`slice`を呼び出し、ファイル内の実際の名前の代わりにその名前の1つで次元を指定することは、ClimaAnalysis v0.5.17で導入されました。

