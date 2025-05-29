```
pascal_triangle(n::Integer [; arr=false [, msg=true]])
```

Row `n` of Pascal triangle, $r_n = [\binom{n}{1},\cdots\ \binom{n}{n}]$

  * `arr` : output full Pascal triangle
  * `msg` : integer-overflow protection (IOP) - warning on activation

(for `n > 10000`)

#### Examples:

```
julia> [pascal_triangle(n) for n=0:5]
6-element Vector{Vector{Int64}}:
 [1]
 [1, 1]
 [1, 2, 1]
 [1, 3, 3, 1]
 [1, 4, 6, 4, 1]
 [1, 5, 10, 10, 5, 1]

julia> pascal_triangle(5; arr=true)
5-element Vector{Vector{Int64}}:
 [1, 1]
 [1, 2, 1]
 [1, 3, 3, 1]
 [1, 4, 6, 4, 1]
 [1, 5, 10, 10, 5, 1]
```
