```
    CDRect
```

`CosArray` representation of a rectangle in the lower left and upper right point format

*Note*: `CDRect` maps to a `Rect` object in the `Rectangle` package. 

# Example

```
julia> CDRect(CosArray(CosObject[CosInt(0), CosInt(0), CosInt(840), CosFloat(640)]))
Rect:[0.0 0.0 840.0 640.0]
```
