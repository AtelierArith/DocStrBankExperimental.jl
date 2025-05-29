```
prettypoly(points::Vector{Point}, vertexfunction = () -> circle(O, 2, :stroke);
    action=:none,
    close=false,
    reversepath=false,
    vertexlabels = (n, l) -> ()
    )
```

Draw the polygon defined by `points`, possibly closing and reversing it, using the current parameters, and then evaluate the `vertexfunction` function at every vertex of the polygon.

The default vertexfunction draws a 2 pt radius circle.

To mark each vertex of a polygon with a randomly colored filled circle:

```julia
p = star(O, 70, 7, 0.6, 0, vertices=true)
prettypoly(p, action=:fill, () ->
    begin
        randomhue()
        circle(O, 10, :fill)
    end,
    close=true)
```

The optional keyword argument `vertexlabels` lets you supply a function with two arguments that can access the current vertex number and the total number of vertices at each vertex. For example, you can label the vertices of a triangle "1 of 3", "2 of 3", and "3 of 3" using:

```julia
prettypoly(triangle, action=:stroke,
    vertexlabels = (n, l) -> (text(string(n, " of ", l))))
```
