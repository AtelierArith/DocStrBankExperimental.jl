```
describe(set <: SBSet; mark=nothing, collect=nothing) :: String
```

セットを説明する文字列を返します

# 例

```julia
julia> I = @setbuild(Integer)
TypeSet(Integer)

julia> P = @setbuild(x in I, 0 <= x < 10)
PredicateSet((x ∈ TypeSet(Integer)) where 0 <= x < 10)

julia> println(describe(P))
{ x ∈ A | 0 <= x < 10 }, where
    A = { x ∈ ::Integer }
```

# キーワード

**`mark`** はマークを適用するセットを指定します。ユーザーはセットとマーク文字列のタプルを割り当てることでマークの文字を変更することもできます。

```julia
julia> println(describe(P, mark=(I, "## ")))
{ x ∈ A | 0 <= x < 10 }, where
 ## A = { x ∈ ::Integer }
```
