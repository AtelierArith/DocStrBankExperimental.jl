```
Nullable(x, hasvalue::Bool=true)
```

値 `x` を `Nullable` 型のオブジェクトでラップします。これは、値が存在するかどうかを示します。`Nullable(x)` は非空のラッパーを返し、`Nullable{T}()` は型 `T` の値を含む可能性のあるラッパーの空のインスタンスを返します。

`Nullable(x, false)` は `Nullable{typeof(x)}()` を返し、結果の `value` フィールドに `x` が格納されます。

# 例

```jldoctest
julia> Nullable(1)
Nullable{Int64}(1)

julia> Nullable{Int64}()
Nullable{Int64}()

julia> Nullable(1, false)
Nullable{Int64}()

julia> dump(Nullable(1, false))
Nullable{Int64}
  hasvalue: Bool false
  value: Int64 1
```
