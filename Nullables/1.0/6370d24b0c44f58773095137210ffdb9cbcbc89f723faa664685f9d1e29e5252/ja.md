```
unsafe_get(x)
```

[`Nullable`](@ref) `x` の値を返します。その他の `x` については `x` を返します。

このメソッドは、`x::Nullable` の値にアクセスしようとする前に `x` が null であるかどうかをチェックしません（したがって「unsafe」です）。

# 例

```jldoctest
julia> x = Nullable(1)
Nullable{Int64}(1)

julia> unsafe_get(x)
1

julia> x = Nullable{String}()
Nullable{String}()

julia> unsafe_get(x)
ERROR: UndefRefError: access to undefined reference
Stacktrace:
 [1] unsafe_get(::Nullable{String}) at ./nullable.jl:152

julia> x = 1
1

julia> unsafe_get(x)
1
```
