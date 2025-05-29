```
copy_if_mutable(x)
```

`x`のコピーを返します。このコピーは`x`を変更することなく、MultableArithmeticsのAPIで変更可能です。もし`mutability(x)`が`IsNotMutable`であれば、`x`は変更できないためそのまま返されます。そうでなければ、[`mutable_copy`](@ref)にリダイレクトされます。可変型はこの関数のメソッドを実装すべきではなく、代わりに[`mutable_copy`](@ref)のメソッドを実装すべきです。
