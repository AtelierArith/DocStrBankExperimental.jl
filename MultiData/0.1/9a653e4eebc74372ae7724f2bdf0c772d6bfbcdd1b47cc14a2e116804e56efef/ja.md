```
≈(md1, md2)
isapprox(md1, md2)
```

2つの `AbstractMultiDataset` が類似しているかどうかを判断します。つまり、同じ変数のグループと変数を持っているかどうかです。これはインスタンスに対するチェックは行われないことに注意してください。

2つの `AbstractMultiDataset` が同じ順序で同じインスタンスを持っているかどうかを確認する場合は、[`isequal`](@ref) を代わりに使用してください。2つの `AbstractMultiDataset` が順序に関係なく同じインスタンスを持っているかどうかを確認する場合は、[`isapproxeq`](@ref) を代わりに使用してください。
