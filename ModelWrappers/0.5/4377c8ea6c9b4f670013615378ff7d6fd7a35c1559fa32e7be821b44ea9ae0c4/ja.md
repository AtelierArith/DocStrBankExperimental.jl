```julia
abstract type FlattenTypes
```

異なるタイプのフラット化をディスパッチするためのスーパタイプ。すべての入力がフラット化されているか（FlattenAll）、または連続値のみがフラット化されているか（FlattenContinuous）を判断します。

# フィールド
