```
ntile(x, n::Integer)
```

Break the input vector into `n` equal-sized buckets.

`ntile()` is a rough rank that breaks the input vector into `n` buckets. If `length(x)` is not an integer multiple of `n`, the size of the buckets will differ by up to one, with larger buckets coming first.

Unlike other ranking functions, `ntile()` ignores ties: it will create evenly sized buckets even if the same value of `x` ends up in different buckets.

# Arguments

  * `x`: A vector to rank. By default, the smallest values will get the smallest ranks. Missing values will be given rank `missing`.
  * `n`: Number of groups to bucket into.

# Examples

```jldoctest
julia> x = [5,1,3,2,2, missing]
6-element Vector{Union{Missing, Int64}}:
 5
 1
 3
 2
 2
  missing

julia> ntile(x, 2)
6-element Vector{Union{Missing, Int64}}:
 2
 1
 2
 1
 1
  missing

julia> ntile(x, 4)
6-element Vector{Union{Missing, Int64}}:
 4
 1
 3
 1
 2
  missing

julia> ntile(1:8, 3)
8-element Vector{Int64}:
 1
 1
 1
 2
 2
 2
 3
 3

julia> df = DataFrame(a = 1:8);

julia> @chain df begin
       @mutate(buckets = ntile(a, 3))
       end
8×2 DataFrame
 Row │ a      buckets 
     │ Int64  Int64   
─────┼────────────────
   1 │     1        1
   2 │     2        1
   3 │     3        1
   4 │     4        2
   5 │     5        2
   6 │     6        2
   7 │     7        3
   8 │     8        3
```
