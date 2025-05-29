```
GreaterThanZero()
```

`<=` または `≤` がマクロ内で使用されるときに intercept するために使用される構造体です。 [`operator_to_set`](@ref) を介して。

この構造体は [`Nonpositives`](@ref) とは異なるため、`x <= y` と `x - y in Nonpositives()` を区別できます。

この構造体は一般的な使用を意図していませんが、一部の JuMP 拡張にとっては便利かもしれません。

## 例

```jldoctest
julia> operator_to_set(error, Val(:<=))
LessThanZero()
```
