```
Repeat(; [row::Vector], [column::Vector], [layer::Vector])
Repeat(field::Vector{SymbolOrString}; columns::Int=nothing)
```

`RepeatSpec`を繰り返し仕様のために作成します。 [](https://vega.github.io/vega-lite/docs/repeat.html)。`field`は位置引数として渡すことができるか、`row`/`column/layer`キーワード引数で渡す必要があります。

# 例

```
Repeat([:Horsepower, :Miles_per_Gallon, :Acceleration], columns=2)
Repeat(column=[:distance, :delay, :time])
```
