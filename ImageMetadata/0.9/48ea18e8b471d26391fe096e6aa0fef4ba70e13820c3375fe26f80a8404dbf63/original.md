```
arraydata(img::ImageMeta) -> array
```

Extract the data from `img`, omitting the properties dictionary. `array` shares storage with `img`, so changes to one affect the other.

See also: [`properties`](@ref).
