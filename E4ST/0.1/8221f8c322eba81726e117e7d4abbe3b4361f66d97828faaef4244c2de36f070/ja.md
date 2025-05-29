```
comparison(value, v) -> comp::Function
```

`value`を`v`の各メンバーと比較するための適切な比較関数を返します。

```
comparison(value, ::Type) -> comp::Function
```

`value`を2番目の引数の型と比較するための適切な比較関数を返します。以下はいくつかのオプションです：

  * comparison(f::Function, ::Type) -> f
  * comparison(s::String, ::Type{<:AbstractString}) -> ==(s)
