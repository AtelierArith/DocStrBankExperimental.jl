```
internal_semi_infinite_variable(vref::SemiInfiniteVariableRef,
                                key::Val{:my_ext_key})::SemiInfiniteVariable
```

`vref`が最適化モデル内の測定拡張中に作成された内部変数であると仮定して、`vref`の半無限変数オブジェクトを返します。これは、`add_measure_variable`と`expand_measure`の組み合わせを利用する最適化モデル拡張に適用されます。
