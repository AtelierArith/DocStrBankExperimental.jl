```
enumsettype(::Type{E})::Type
```

列挙型 `E` のインスタンスを格納するのに適した `EnumSet` のサブタイプを返します。典型的な使用法は次のようになります：

```julia
@enum Alphabet A B C
const MySet = enumsettype(Alphabet)

ab = MySet((A, B))
bc = MySet((B, C))
ab ∩ bc
...
```
