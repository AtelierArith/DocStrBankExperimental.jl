```
shareproperties(img::ImageMeta, data) -> imgnew
```

Create a new "image," reusing the properties dictionary of `img` but using the data of the AbstractArray `data`. The two images have synchronized properties; modifying one also affects the other.

See also: [`copyproperties`](@ref).
