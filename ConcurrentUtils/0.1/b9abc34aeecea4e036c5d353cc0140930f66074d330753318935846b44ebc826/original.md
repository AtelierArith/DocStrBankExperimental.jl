```
try_race_put!(promise::Promise{T}, value) -> Ok(value′::T) or Err(existing::T)
```

Try to set a `value` in the `promise`.

Since the `value` is converted to `T` first, the returned `value′` may not be identical to the input `value`.

# Extended help

## Examples

```jldoctest ConcurrentUtils2
julia> using ConcurrentUtils

julia> p = Promise{Int}();

julia> try_race_put!(p, 123)
Try.Ok: 123

julia> try_race_put!(p, 456)
Try.Err: 123
```
