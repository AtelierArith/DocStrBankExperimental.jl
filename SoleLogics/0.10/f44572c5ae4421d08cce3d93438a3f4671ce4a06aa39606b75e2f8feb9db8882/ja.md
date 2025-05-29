```
isbot(::Truth)::Bool
```

`Truth` 値がその代数のボトムである場合は true を返します。たとえば、クリスプなケースでは、`Bool` 真理値の場合、次のようになります：

```
isbot(t::Bool)::Bool = (t == false)
```

[`istop`](@ref) や [`Truth`](@ref) も参照してください。
