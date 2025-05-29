```
copyproperties(img::ImageMeta, data) -> imgnew
```

Create a new "image," copying the properties dictionary of `img` but using the data of the AbstractArray `data`. Note that changing the properties of `imgnew` does not affect the properties of `img`.

See also: [`shareproperties`](@ref).
