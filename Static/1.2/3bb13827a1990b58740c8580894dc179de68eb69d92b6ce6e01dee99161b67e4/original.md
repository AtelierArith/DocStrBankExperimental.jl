```
static_promote(x::AbstractRange{<:Integer}, y::AbstractRange{<:Integer})
```

A type stable method for combining two equal ranges into a new range that preserves static parameters. Throws an error if `x != y`.

# Examples

```julia
julia> static_promote(static(1):10, 1:static(10))
static(1):static(10)

julia> static_promote(1:2:9, static(1):static(2):static(9))
static(1):static(2):static(9)
```
