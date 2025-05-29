```
TransformedKernel(k::Kernel, t::Transform)
```

`k`から派生したカーネルで、入力は[`Transform`](@ref) `t`を介して変換されます。

入力変換を伴うカーネルを作成するための推奨される方法は、`TransformedKernel`を直接使用するのではなく、合成演算子[`∘`](@ref)またはそのエイリアス`compose`を使用することです。これにより、特定のカーネルと変換に対する最適化された実装が可能になります。

参照: [`∘`](@ref)
