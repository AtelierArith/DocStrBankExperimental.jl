```
istop(::Truth)::Bool
```

`Truth` 値がその代数の上限である場合に true を返します。たとえば、クリスプな場合、`Bool` 真理値を使用すると、次のようになります：

```
istop(t::Bool)::Bool = (t == true)
```

[`isbot`](@ref) や [`Truth`](@ref) も参照してください。
