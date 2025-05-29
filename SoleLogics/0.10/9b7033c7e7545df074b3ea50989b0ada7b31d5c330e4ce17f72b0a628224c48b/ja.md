```
check(a::Atom, i::AbstractDict)
```

渡された原子に対応するブール値を返します。

# 例

```julia-repl
julia> check(Atom(1), Dict([1 => ⊤, 2 => ⊥]))
true

julia> check(Atom(3), Dict([1 => ⊤, 2 => ⊥]))
false
```

[`Atom`](@ref)も参照してください。
