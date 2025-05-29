```
@iv_str -> Interval
```

Construct an interval with mathematical notation such as `iv"(1,2]"`.

# Examples

```jldoctest
julia> iv"[1,2]"
1 .. 2

julia> iv"[1,2)"
1 .. 2 (closed-open)

julia> iv"(1,2]"
1 .. 2 (open-closed)

julia> iv"(1,2)"
1 .. 2 (open)
```
