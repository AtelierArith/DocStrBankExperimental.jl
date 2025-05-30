```
GreaterThanZero()
```

`>=` または `≥` がマクロ内で使用されるときに intercept するために使用される構造体です。 [`operator_to_set`](@ref) を介して。

この構造体は [`Nonnegatives`](@ref) とは異なるため、`x >= y` と `x - y in Nonnegatives()` を区別できます。

この構造体は一般的な使用を意図していませんが、一部の JuMP 拡張にとっては有用かもしれません。

## 例

```jldoctest
julia> operator_to_set(error, Val(:>=))
GreaterThanZero()
```
