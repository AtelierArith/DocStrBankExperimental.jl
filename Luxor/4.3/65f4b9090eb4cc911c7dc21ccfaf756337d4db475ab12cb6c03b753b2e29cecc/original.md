```
p = Partition(areawidth, areaheight, tilewidth, tileheight)
```

A Partition is an iterator that, for each iteration, returns a tuple of:

  * the `x`/`y` point of the center of each tile in a set of tiles that divide up a rectangular space such as a page into rows and columns (relative to current 0/0)
  * the number of the tile

`areawidth` and `areaheight` are the dimensions of the area to be tiled, `tilewidth`/`tileheight` are the dimensions of the tiles.

Tiler and Partition are similar:

  * Partition lets you specify the width and height of a cell
  * Tiler lets you specify how many rows and columns of cells you want, and a margin

    ```julia
    tiles = Partition(1200, 1200, 30, 30)
    for (pos, n) in tiles

        # the point pos is the center of the tile

    end
    ```

You can access the calculated tile width and height like this:

```julia
tiles = Partition(1200, 1200, 30, 30)
for (pos, n) in tiles
    ellipse(pos.x, pos.y, tiles.tilewidth, tiles.tileheight, :fill)
end
```

It's sometimes useful to know which row and column you're currently on:

```
tiles.currentrow
tiles.currentcol
```

should have that information for you.

Unless the tilewidth and tileheight are exact multiples of the area width and height, you'll see a border at the right and bottom where the tiles won't fit.
