```
term(x)
```

引数を適切な `AbstractTerm` 型でラップします： `Symbol` と `AbstractString` は `Term` になり、`Number` は `ConstantTerm` になります。 すべての `AbstractTerm` は変更されません。 `AbstractString` はラップする前にシンボルに変換されます。

# 例

```jldoctest
julia> ts = term.((1, :a, "b"))
1
a(unknown)
b(unknown)

julia> typeof(ts)
Tuple{ConstantTerm{Int64}, Term, Term}
```
