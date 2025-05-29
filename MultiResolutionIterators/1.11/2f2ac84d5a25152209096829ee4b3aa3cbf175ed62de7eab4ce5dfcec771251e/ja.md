```
consolidate(xs)
```

これは collect の一般化です。慣例として `collect(::T)::Vector{eltype{T}}` があります。`consolidate` はより弱い慣例を持ち、`getindex` が機能する何らかの型を返すべきです。正確には、`consolidate(::T)::V` に対して `eltype(V)==eltype(T)` であり、`∀i` に対して `getindex(collect(xs), ii) == getindex(consolidate(xs), ii)` です。

ほとんどの型ではデフォルトで `collect` が使用されます。さまざまな `Char` の系列に対しては、それらを文字列に変換します。

動作を変更したい場合はオーバーロードできます。特に、あなたの型のインデックス可能なコピーを作成する安価な方法がある場合（例えば、あなたの型が不変の場合）です。

例えば：

```julia
struct MyType # 悪い型ですが、何でも
    content
    field
end
MultiResolutionIterators.consolidate(xs::MyType) == MyType(consolidate(xs.content), xs.field)
```

型に保持したい他のフィールドがある場合に便利です。
