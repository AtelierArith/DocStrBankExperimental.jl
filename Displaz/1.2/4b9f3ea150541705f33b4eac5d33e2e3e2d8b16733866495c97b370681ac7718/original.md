Add 3D points or lines to the current plot.

```
  plot3d([plotobj,] position; attr1=value1, ...)
```

The `position` array should be a set of N vertex positions, specified as 3xN array or a `Vector` of `FixedVector{3}`.  The `plotobj` argument is optional and determines which plot window to send the data to.  If it's not used the data will be sent to the plot window returned by `current()`.

TODO: Revisit the nasty decision of the shape of position again - the above choice is somewhat inconsistent with supplying markersize / markershape as a column vector :-(  Can we have a set of consistent broadcasting rules for this? It seems like the case of a 3x3 matrix will always be ambiguous if we try to guess what the user wants.

### Data set attributes

The following attributes can be attached to a dataset on each call to `plot3d`:

  * `label` - A string labeling the data set

### Vertex attributes

Each point may have a set of vertex attributes attached to control the visual representation and tag the point for inspection. You can pass any `Vector` of `Float32` values for any custom information you like, but the following are supported by the default shader:

  * `color`       - A color or vector of colors for each point; see below for                 ways to specify these.
  * `intensity`   - A vector of the intensity of each point (between 0 and 1)
  * `markersize`  - Vertex marker size
  * `markershape` - Vector of vertex marker shapes.  Shape can be represented                 either by a Char or a numeric identifier between 0 and 4:

```
                    sphere - '.' 0    square - 's' 1
                    circle - 'o' 2    times  - 'x' 3
                    cross  - '+' 4
```

#### Specifying colors

Colors may be provided in any of three ways:

  * As instances of types from the ColorTypes package, for example, HSV(180,1,1). These are converted to RGB using the RGB constructor.
  * As a `Vector` of three elements, red, green and blue, between 0.0 and 1.0.
  * Using a matlab-like single color letter name string or `Char`.  Supported are red, green, blue, cyan, magenta, yellow, black and white; all are abbreviated with the first letter of the color name except black for which 'k' is used.

A color per point may be supplied as a `Vector` of `Color` subtypes or a 3xN matrix with red, green and blue in the rows.

### Plotting points

To plot 10000 random points with distance from the origin determining the color, and random marker shapes:

```
  P = randn(3,10000)
  c = 0.5./sumabs2(P,1) .* [1,0,0]
  plot3d(P, color=c, markershape=rand(1:4,10000))
```

### Plotting lines

To plot a piecewise linear curve between 10000 random vertices

```
  plot3d(randn(3,10000), markershape="-")
```

When plotting lines, the `linebreak` keyword argument can be used to break the position array into multiple line segments.  Each index in the line break array is the initial index of a line segment.
