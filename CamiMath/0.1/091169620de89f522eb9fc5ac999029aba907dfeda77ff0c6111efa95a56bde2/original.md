```
integer_partitions(n [,m [; transpose=false [, count=false]]])
```

`default`                      : The integer partitions of `n`

`count`                        : The number of integer partitions of `n`

`transpose` = `false` (`m` > 0): partitions restricted to maximum part `m`             = `true`  (`m` > 0): partitions restricted to maximum length `m``

definitions:

The integer partition of the positive integer `n` is a nonincreasing sequence of positive integers p1, p2,... pk whose sum is `n`. The elements of the sequence are called the parts of the partition.

#### Examples:

```
julia> integer_partitions(7)
15-element Vector{Vector{Int64}}:
 [1, 1, 1, 1, 1, 1, 1]
 [2, 2, 2, 1]
 [2, 2, 1, 1, 1]
 [2, 1, 1, 1, 1, 1]
 [3, 3, 1]
 [3, 2, 2]
 [3, 2, 1, 1]
 [3, 1, 1, 1, 1]
 [4, 3]
 [4, 2, 1]
 [4, 1, 1, 1]
 [5, 2]
 [5, 1, 1]
 [6, 1]
 [7]

julia> integer_partitions(7; count=true)
15

julia> integer_partitions(7, 4; count=true)
3

julia> integer_partitions(7, 4)
3-element Vector{Vector{Int64}}:
 [4, 3]
 [4, 2, 1]
 [4, 1, 1, 1]

julia> integer_partitions(7, 4; transpose=true)
3-element Vector{Vector{Int64}}:
 [2, 2, 2, 1]
 [3, 2, 1, 1]
 [4, 1, 1, 1]
```
