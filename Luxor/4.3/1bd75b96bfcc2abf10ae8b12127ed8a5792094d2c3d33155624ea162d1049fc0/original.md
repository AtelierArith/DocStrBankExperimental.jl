```
getcells(t, rows, columns)
```

Get the Tiler or Table cells in `t` corresponding to `rows` and `columns`.

  * `t` is a Tiler or Table
  * `rows` is an array or range of row numbers
  * `cols` is an array or range of column numbers

Use `:` for "all rows" or "all columns".

Returns an array of Tuples, where each Tuple is `(Point, Number)`.

`markcells()` can use the result of this function to mark selected cells.

## Example

```julia
@draw begin
    chessboard = Tiler(600, 600, 8, 8)
    # odd rows odd columns
    s = getcells(chessboard, 1:2:12, 1:2:12)
    markcells(chessboard, s, action = :fill)
    # even rows even columns
    s = getcells(chessboard, 2:2:12, 2:2:12)
    markcells(chessboard, s, action = :fill)
end
```
