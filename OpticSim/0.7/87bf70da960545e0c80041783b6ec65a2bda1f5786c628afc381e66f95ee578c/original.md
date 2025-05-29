```
reset!(a::HierarchicalImage{T})
```

Resets the pixels in the image to `zero(T)`. Do this rather than `image .= zero(T)` because that will cause every pixel to be accessed, and therefore allocated. For large images this can cause huge memory traffic.
