```
Container{T}
```

Intermediate container for a `struct` object when serializing/deserializing it.

```
Container{T}()
```

Create an uninitialized container for `T`.

# Examples

```jldoctest
julia> Container{Complex{Int64}}()
Container{Complex{Int64}}:
  re: Int64 = #undef
  im: Int64 = #undef
```
