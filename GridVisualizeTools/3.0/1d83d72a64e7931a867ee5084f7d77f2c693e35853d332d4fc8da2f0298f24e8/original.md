```julia
marching_triangles(
    coord,
    cellnodes,
    func,
    lines,
    levels;
    Tc,
    Tp,
    Tv
)

```

March through the given grid and extract points and values for given iso-line levels and/or given intersection lines. From the returned point list and value list a line plot can be created.

Input:     coord: matrix storing the coordinates of the grid     cellnodes: connectivity matrix     func: function on the grid nodes to be evaluated     lines: vector of line definitions [a,b,c], s.t., ax + by + c = 0 defines a line     levels: vector of levels for the iso-surface     Tc: scalar type of coordinates     Tp: vector type of coordinates     Tv: scalar type of function values

Output:     points: vector of 2D points of the intersections of the grid with the iso-surfaces or lines     adjacencies: vector of 2D vectors storing connected points in the grid     value: interpolated values of `func` at the intersection points

Note that passing both nonempty `lines` and `levels` will create a result with both types of points mixed.
