```
pix_read_png(
    data::AbstractArray{UInt8}
)::Union{Pix, Nothing}
```

Read a PNG image from the byte array.  Returns `nothing` on error.

**Arguments:**

| T   | Name | Default | Description                                |
|:--- |:---- |:------- |:------------------------------------------ |
| R   | data |         | The byte array to read the PNG image from. |
