```julia
next_offset_divisible_prime(
    n::Int64,
    offset::Int64,
    divisor::Int64,
    tries::Int64
) -> Int64

```

次の素数 `p` を取得します。これは `n` から始まり、`(p + offset) % divisor == 0` が成り立ちます。

```jldoctest
julia> next_offset_divisible_prime(3, 1, 4, 1000)
3

julia> next_offset_divisible_prime(5, 1, 4, 1000)
7

julia> next_offset_divisible_prime(4, 1, 4, 1000)
7

```
