```
XorNot(property::AbstractString) <: QueryOperation
```

[`Xor`](@ref)と同様ですが、マスクの逆を使用します。文字列[`Query`](@ref)では、`^!`演算子を使用し、その後にマスクを計算するために参照する軸プロパティの名前を続けます。
