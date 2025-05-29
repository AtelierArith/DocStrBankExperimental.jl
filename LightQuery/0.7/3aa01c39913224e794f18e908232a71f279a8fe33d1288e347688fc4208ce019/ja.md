```
function reduce_rows(rows, a_function, columns...)
```

`rows`の各`columns`に対して関数を適用します。

```jldoctest
julia> using LightQuery


julia> using Test: @inferred


julia> @inferred reduce_rows(Rows(a = [1, 1], b = [1.0, 1.0]), +, name"a", name"b")
(a = 2, b = 2.0)
```
