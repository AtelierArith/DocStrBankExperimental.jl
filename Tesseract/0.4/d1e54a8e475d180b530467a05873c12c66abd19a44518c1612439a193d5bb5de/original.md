```
pix_read(
    data::AbstractArray{UInt8}
)::Union{Pix, Nothing}
```

Load an image from from a byte array.  Returns `nothing` if the file could not be loaded.

**Arguments:**

| T   | Name | Default | Description                            |
|:--- |:---- |:------- |:-------------------------------------- |
| R   | data |         | The byte array to read the image from. |
