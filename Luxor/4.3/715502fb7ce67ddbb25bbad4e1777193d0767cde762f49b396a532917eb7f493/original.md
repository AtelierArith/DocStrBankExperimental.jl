```
getcells(t, n::Int)
```

Get the cell `n` in Tiler or Table `t`.

Returns an array of Tuples, where each Tuple is `(Point, Number)`.

!!! note
    Luxor Tables and Tilers are numbered by row then column, rather than the usual Julia column-major numbering:


```
 1  2  3  4  5
 6  7  8  9 10
11 12 13 14 15
16 17 18 19 20
```
