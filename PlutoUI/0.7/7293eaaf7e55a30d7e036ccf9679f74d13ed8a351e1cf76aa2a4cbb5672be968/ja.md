```
WithIOContext(x, properties::Pair...)
```

`x`の表示のために設定された追加のIOContextプロパティを持つ`x`のラッパーです。

!!! compat "PlutoUI 0.7.52"
    PlutoUI 0.7.52以前は、`x`は`properties`からのプロパティのみを使用して表示され、レンダリングに使用されるIOContextからのプロパティは無視されていました。これは修正されました。


# 例

```julia
WithIOContext(rand(100,100), :compact => false)
```

```julia
large_df = DataFrame(rand(100,100))
WithIOContext(large_df, :displaysize => (9999,9999))
```
