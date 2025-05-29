```
@trait SomeMeasureType trait1=value1 trait2=value2 ...
```

`SomeMeasureType`を測定値のインスタンスを持つ型として宣言し、指定された特性をすべてのそのようなインスタンスで与えられた値を持つようにオーバーロードします。

例えば、`AUC`が型である場合、次のようになります。

```
@trait AUC orientation = Loss() supports_weights = true
```

これは次の宣言と同等です。

```
StatisticalMeasuresBase.is_measure(::AUC) = true
StatisticalMeasuresBase.orientation(::AUC) = Score()
StatisticalMeasuresBase.supports_weights(::AUC) = true
```
