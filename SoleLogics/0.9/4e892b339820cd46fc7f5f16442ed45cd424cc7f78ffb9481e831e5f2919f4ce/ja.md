```
@atoms(ps...)
```

[`Atom`](@ref)のコレクションをインスタンス化し、それらをベクターとして返します。

!!! info
    このマクロでインスタンス化された原子は、グローバルスコープで定数として定義されます。


# 例

```julia-repl
julia> SoleLogics.@atoms String p q r s
4-element Vector{Atom{String}}:
 Atom{String}("p")
 Atom{String}("q")
 Atom{String}("r")
 Atom{String}("s")

julia> p
Atom{String}("p")
```
