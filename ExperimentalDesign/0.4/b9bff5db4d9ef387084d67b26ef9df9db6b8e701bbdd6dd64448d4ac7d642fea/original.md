```julia
next_offset_divisible_prime(
    n::Int64,
    offset::Int64,
    divisor::Int64,
    tries::Int64
) -> Int64

```

Gets the next prime `p`, starting from `n`, for which `(p + offset) % divisor == 0` holds.

```jldoctest
julia> next_offset_divisible_prime(3, 1, 4, 1000)
3

julia> next_offset_divisible_prime(5, 1, 4, 1000)
7

julia> next_offset_divisible_prime(4, 1, 4, 1000)
7

```
