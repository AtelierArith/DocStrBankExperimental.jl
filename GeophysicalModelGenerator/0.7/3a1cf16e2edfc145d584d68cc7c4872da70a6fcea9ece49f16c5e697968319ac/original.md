```
struct ProjectionPoint
    Lon     :: Float64
    Lat     :: Float64
    EW      :: Float64
    NS      :: Float64
    zone    :: Integer
    isnorth :: Bool
end
```

Structure that holds the coordinates of a point that is used to project a data set from Lon/Lat to a Cartesian grid and vice-versa.
