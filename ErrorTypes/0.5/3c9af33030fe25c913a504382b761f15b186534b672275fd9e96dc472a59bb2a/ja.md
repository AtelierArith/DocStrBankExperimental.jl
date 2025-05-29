```
is_ok_and(f, x::Result)::Bool
```

`x`が結果値であり、`f(unwrap(x))`をチェックします。`f(unwrap(x))`は`Bool`を返さなければなりません。

# 例

```
julia> is_ok_and(isodd, none(Int))
false

julia> is_ok_and(isodd, some(2))
false

julia> is_ok_and(isodd, Result{Int, String}(Ok(9)))
true

julia> is_ok_and(ncodeunits, some("Success!"))
ERROR: TypeError: non-boolean (Int64) used in boolean context
```
