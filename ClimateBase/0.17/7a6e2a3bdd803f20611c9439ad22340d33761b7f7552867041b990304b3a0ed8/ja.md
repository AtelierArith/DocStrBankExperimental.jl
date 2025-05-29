```
hemispheric_functions(A::ClimArray) → north, south
```

配列 `north, south` を返します。`A` を北半球と南半球に分割し、`south` の緯度を適切に変換して、両方の配列が同じ緯度次元を持つようにします（したがって、比較や操作を行うことができます）。
