```
poly(pointlist::Vector{Point}, action = :none;
    close=false,
    reversepath=false)
```

Draw a polygon. Create a path with the points in `pointlist` and apply `action`. By default `poly()` doesn't close or fill the polygon.
