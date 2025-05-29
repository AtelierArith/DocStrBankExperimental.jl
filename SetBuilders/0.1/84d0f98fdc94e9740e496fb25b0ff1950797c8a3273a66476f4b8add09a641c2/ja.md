```
ismember(elem, set <: SBSet; on_member::Function, on_nomember::Function)
```

`elem` が `set` のメンバーである場合は `true` を返します。そうでない場合は false を返します。

# キーワード

## `on_member`

`on_member` に登録されたコールバック関数は、`elem` が `set` のメンバーであることが知られているときに呼び出されます。

## `on_nomember`

`on_nomember` に登録されたコールバック関数は、`elem` が `set` のメンバーでないことが知られているときに呼び出されます。

```julia
julia> I = @setbuild(Integer)
TypeSet(Integer)

julia> P = @setbuild(x in I, 0 <= x < 10)
PredicateSet((x ∈ TypeSet(Integer)) where 0 <= x < 10)

julia> F = h -> println(describe(h[1].set, mark=h[end].set))
#7 (generic function with 1 method)

julia> ismember(-1, P, on_nomember=F)
=> { x ∈ A | 0 <= x < 10 }, where
    A = { x ∈ ::Integer }
false
```
