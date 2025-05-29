```
@scheme f g h1 h2 ...
```

ネストされた `ExtendScheme` を構築するためのマクロで、形式は `ExtendScheme(ExtendScheme(Scheme(f, g), h1), h2)` です。まずベース（`Scheme(f, g)`）を形成し、その後 `ExtendScheme(s, h)` でラップして、すべての末尾の `h` が使い果たされるまで続けます。

# 例

```jldoctest
julia> (@scheme sum last first) == ExtendScheme(Scheme(sum, last), first)
true

julia> (@scheme sum last first last first) == ExtendScheme(ExtendScheme(ExtendScheme(Scheme(sum, last), first), last), first)
true
```
