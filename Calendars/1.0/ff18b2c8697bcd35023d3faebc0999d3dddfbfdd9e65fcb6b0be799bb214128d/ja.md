```julia
isValidDate(date::CDate, warn=true)::Bool
```

与えられた `date` が有効なカレンダー日付であるかを確認します。

例えば：

```julia
julia> isValidDate("Gregorian", 1756, 1, 27) 
```

また、次のように書くこともできます。

```julia
julia> isValidDate(CE, 1756, 1, 27) 
```

このクエリは、1756-01-27 が有効なグレゴリオ日付であることを確認します。しかし、次の2つのクエリはそれぞれ 'false' と 'true' を返します。

```julia
julia> isValidDate(CE, 1900, 2, 29)

julia> isValidDate(JD, 1900, 2, 29)
```
