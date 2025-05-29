```
Substitute(condition) -> substitute(f(expr), expr)
```

`condition(expr)` が真であれば `expr` を `f(expr)` に置き換える関数を返します。すべてのサブ式に再帰的に適用されます。

# 例

```jldoctest
julia> sub = Substitute() do expr
           expr isa Symbol && expr in [:x] && return true
           return false
       end;

julia> sub(_->1, :(x + y))
:(1 + y)
```
