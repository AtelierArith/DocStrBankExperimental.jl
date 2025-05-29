```
polysmooth(points, radius, action=:action; debug=false, close=true)
polysmooth(points, radius; action=:none, debug=false, close=true)
```

Make a closed path from the `points` and round the corners by making them arcs with the given radius. Execute the action when finished.

The arcs are sometimes different sizes: if the given radius is bigger than the length of the shortest side, the arc can't be drawn at its full radius and is therefore drawn as large as possible (as large as the shortest side allows).

The `debug` option also draws the construction circles at each corner.

TODO Return something more useful than a Boolean.
