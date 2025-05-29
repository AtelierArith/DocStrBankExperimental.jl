```
tiles = Tiler(areawidth, areaheight, nrows, ncols, margin=20)
```

A Tiler is an iterator that, for each iteration, returns a tuple of:

  * the `x`/`y` point of the center of each tile in a set of tiles that divide up a rectangular space such as a page into rows and columns (relative to current 0/0)
  * the number of the tile

`areawidth` and `areaheight` are the dimensions of the area to be tiled, `nrows`/`ncols` are the number of rows and columns required, and `margin` is applied to all four edges of the area before the function calculates the tile sizes required.

Tiler and Partition are similar:

  * Partition lets you specify the width and height of a cell
  * Tiler lets you specify how many rows and columns of cells you want, and a margin:

```julia
tiles = Tiler(1000, 800, 4, 5, margin=20)
for (pos, n) in tiles
    # the point pos is the center of the tile
end
```

You can access the calculated tile width and height like this:

```julia
tiles = Tiler(1000, 800, 4, 5, margin=20)
for (pos, n) in tiles
    ellipse(pos.x, pos.y, tiles.tilewidth, tiles.tileheight, :fill)
end
```

It's sometimes useful to know which row and column you're currently on. `tiles.currentrow` and `tiles.currentcol` should have that information for you.

To use a Tiler to make grid points:

```julia
first.(collect(Tiler(800, 800, 4, 4)))
```

which returns an array of points that are the center points of the grid.
