```
linearspace(start::T, stop::T, N::Int)  where {T<:Number}
```

Generate linear space.

Generate a linear sequence of `N` numbers between  `start` and `stop` (i. e. sequence  of number with uniform intervals inbetween).

# Example

```
julia> linearspace(2.0, 3.0, 5)
2.0:0.25:3.0
```
