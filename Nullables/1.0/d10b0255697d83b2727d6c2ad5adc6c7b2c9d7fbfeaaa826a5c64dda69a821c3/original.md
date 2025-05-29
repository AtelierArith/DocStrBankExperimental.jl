```
Nullable(x, hasvalue::Bool=true)
```

Wrap value `x` in an object of type `Nullable`, which indicates whether a value is present. `Nullable(x)` yields a non-empty wrapper and `Nullable{T}()` yields an empty instance of a wrapper that might contain a value of type `T`.

`Nullable(x, false)` yields `Nullable{typeof(x)}()` with `x` stored in the result's `value` field.

# Examples

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
