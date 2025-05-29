```
≊(md1, md2)
isapproxeq(md1, md2)
```

2つの `AbstractMultiDataset` が同じ変数グループ、変数、およびインスタンスを持っているかどうかを判断します。

注意: インスタンスの順序は重要ではありません。

2つの `AbstractMultiDataset` が同じインスタンスを同じ順序で持っているかどうかを確認する場合は、[`isequal`](@ref) を代わりに使用してください。2つの `AbstractMultiDataset` が同じ変数グループと変数を持っているかどうかを確認する場合は、[`isapprox`](@ref) を代わりに使用してください。

TODO レビュー
