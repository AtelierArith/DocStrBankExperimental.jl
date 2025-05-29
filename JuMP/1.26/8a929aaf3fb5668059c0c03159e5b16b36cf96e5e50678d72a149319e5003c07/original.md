```
in_set_string(mode::MIME, set)
```

Return a `String` representing the membership to the set `set` using print mode `mode`.

## Extensions

JuMP extensions may extend this method for new `set` types to improve the legibility of their printing.

## Example

```jldoctest
julia> in_set_string(MIME("text/plain"), MOI.Interval(1.0, 2.0))
"∈ [1, 2]"
```
