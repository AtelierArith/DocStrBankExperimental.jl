```
empty!(collection) -> collection
```

Remove all elements from a `collection`.

# Examples

```jldoctest
julia> A = SwissDict("a" => 1, "b" => 2)
SwissDict{String, Int64} with 2 entries:
  "a" => 1
  "b" => 2

julia> empty!(A);

julia> A
SwissDict{String, Int64}()
```
