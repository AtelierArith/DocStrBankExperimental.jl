```
probabilities!(s, args...)
```

`probabilities(args...)`と似ていますが、一時的に使用されるコンテナ`s`の事前割り当てを可能にします。

特定の推定器にのみ機能します。例えば、[`OrdinalPatterns`](@ref)を参照してください。
