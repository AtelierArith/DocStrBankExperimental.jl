```
Peek(rows, maximum_length = 4)
```

Peek an iterator which returns named tuples. Will show no more than `maximum_length` rows.

```jldoctest Peek
julia> using LightQuery


julia> Peek(Rows(a = 1:5, b = 5:-1:1))
Showing 4 of 5 rows
|   a |   b |
| ---:| ---:|
|   1 |   5 |
|   2 |   4 |
|   3 |   3 |
|   4 |   2 |
```
