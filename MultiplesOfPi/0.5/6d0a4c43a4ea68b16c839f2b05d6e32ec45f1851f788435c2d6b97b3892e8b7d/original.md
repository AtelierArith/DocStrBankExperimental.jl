```
Pi
```

The number `PiExpTimes(1, 1)`, numerically equivalent to `pi`. Using `Pi` instead of `pi` often produces results that avoid floating-point inaccuracies.

# Examples

```jldoctest
julia> sin(2Pi) == 0
true

julia> sin(2π) == 0
false

julia> exp(im*Pi) + 1 == 0
true

julia> exp(im*π) + 1 == 0
false

julia> (2//3)Pi + Pi == (5//3)Pi
true

julia> (2//3)π + π == (5//3)π
false
```
