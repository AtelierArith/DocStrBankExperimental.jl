```
alignsignals(x, y)
```

Use finddelay() and shiftsignal() to time align x to y. Also return the delay of x with respect to y.

# Example

```jldoctest
julia> alignsignals([0, 0, 1, 2, 3], [1, 2, 3])
([1, 2, 3, 0, 0], 2)

julia> alignsignals([1, 2, 3], [0, 0, 1, 2, 3])
([0, 0, 1], -2)
```

See also [`alignsignals!`](@ref).
