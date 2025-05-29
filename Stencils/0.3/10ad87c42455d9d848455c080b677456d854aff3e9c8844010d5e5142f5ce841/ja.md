```
Conditional <: Padding
```

配列のサイズを変更しないパディングですが、範囲外インデックスに対して `getindex` をチェックし、[`Remove`](@ref) で `padval` を挿入するか、[`Wrap`](@ref) を使用して配列の反対側から値を挿入します。
