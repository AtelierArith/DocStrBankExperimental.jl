```
BoundingBox(ul, lr)
```

Construct a bounding box defined by the corners `ul` and `lr`.

All coordinates should be provided in latitude and longitude.

# Parameters

  * `ul`: The upper-left corner of the box as a `Tuple{T,T}` of latitude and longitude.
  * `lr`: The lower-right corner of the box as a `Tuple{T,T}` of latitude and longitude.

# Example

```julia
bb = BoundingBox((52.1, -114.4), (51.9, -114.1))
```
