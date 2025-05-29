```
print_proposition(io, p)
```

与えられた命題を `IOContext` とともに印刷します `:root => false`。

[`print_expression`](@ref Interface.print_expression) から呼び出されるべきです。

# 例

```jldoctest
julia> @atomize print_proposition(stdout, ¬p)
¬p

julia> @atomize print_proposition(stdout, p ∧ q)
(p ∧ q)
```
