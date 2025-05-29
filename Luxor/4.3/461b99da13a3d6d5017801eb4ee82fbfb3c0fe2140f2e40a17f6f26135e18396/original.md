```
t = Table(nrows, ncols)
t = Table(nrows, ncols, colwidth, rowheight)
t = Table(rowheights, columnwidths)
```

Tables are centered at `O`, but you can supply a point after the specifications.

```
t = Table(nrows, ncols, centerpoint)
t = Table(nrows, ncols, colwidth, rowheight, centerpoint)
t = Table(rowheights, columnwidths, centerpoint)
```

## Examples

Simple tables

```
t = Table(4, 3) # 4 rows and 3 cols, default is 100w, 50 h
t = Table(4, 3, 80, 30)   # 4 rows of 30pts high, 3 cols of 80pts wide
t = Table(4, 3, (80, 30)) # same
t = Table((4, 3), (80, 30)) # same
```

Specify row heights and column widths instead of quantities:

```
t = Table([60, 40, 100], 50) # 3 different height rows, 1 column 50 wide
t = Table([60, 40, 100], [100, 60, 40]) # 3 rows, 3 columns
t = Table(fill(30, (10)), [50, 50, 50]) # 10 rows 30 high, 3 columns 10 wide
t = Table(50, [60, 60, 60]) # just 1 row (50 high), 3 columns 60 wide
t = Table([50], [50]) # just 1 row, 1 column, both 50 units wide
t = Table(50, 50, 10, 5) # 50 rows, 50 columns, 10 units wide, 5 units high
t = Table([6, 11, 16, 21, 26, 31, 36, 41, 46], [6, 11, 16, 21, 26, 31, 36, 41, 46])
t = Table(15:5:55, vcat(5:2:15, 15:-2:5))
 #  table has 108 cells, with:
 #  row heights: 15 20 25 30 35 40 45 50 55
 #  col widths:  5 7 9 11 13 15 15 13 11 9 7 5
t = Table(vcat(5:10:60, 60:-10:5), vcat(5:10:60, 60:-10:5))
t = Table(vcat(5:10:60, 60:-10:5), 50) # 1 column 50 units wide
t = Table(vcat(5:10:60, 60:-10:5), 1:5:50)
```

A Table is an iterator that, for each iteration, returns a tuple of:

  * the `x`/`y` point of the center of cells arranged in rows and columns (relative to current 0/0)
  * the number of the cell (left to right, then top to bottom)

`nrows`/`ncols` are the number of rows and columns required.

It's sometimes useful to know which row and column you're currently on while iterating:

```julia
t.currentrow
t.currentcol
```

and row heights and column widths are available in:

```julia
t.rowheights
t.colwidths
```

`box(t::Table, r, c)` can be used to fill table cells:

```julia
@svg begin
    for (pt, n) in (t = Table(8, 3, 30, 15))
        randomhue()
        box(t, t.currentrow, t.currentcol, :fill)
        sethue("white")
        text(string(n), pt)
    end
end
```

or without iteration, using cellnumber:

```julia
@svg begin
    t = Table(8, 3, 30, 15)
    for n in eachindex(t)
        randomhue()
        box(t, n, :fill)
        sethue("white")
        text(string(n), t[n])
    end
end
```

To use a Table to make grid points:

```julia-repl
julia> first.(collect(Table(10, 6)))
60-element Vector{Point}:
 Luxor.Point(-10.0, -18.0)
 Luxor.Point(-6.0, -18.0)
 Luxor.Point(-2.0, -18.0)
 ⋮
 Luxor.Point(2.0, 18.0)
 Luxor.Point(6.0, 18.0)
 Luxor.Point(10.0, 18.0)
```

which returns an array of points that are the center points of the cells in the table.

## Selecting cells

You can select cells using `getcells(table, rows, columns)`. This returns a list of `(point, index)` tuples.

  * `getcells(t, :, :)` returns a list of all cells
  * `getcells(t, 1, :)` returns a list of all cells in row 1
  * `getcells(t, :, 3)` returns a list of all cells in column 3
  * `getcells(t, 2:4, [3, 5])` returns a list of cells in rows 2-4, columns 3 and 5
