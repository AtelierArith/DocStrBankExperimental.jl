`perm(p::Perm)`は`Perm`のデータフィールドを返します。

```julia-repl
julia> perm(Perm(2,3;degree=4))
4-element Vector{Int16}:
 1
 3
 2
 4
```
