```
pix_read_gif(
    data::AbstractArray{UInt8}
)::Union{Pix, Nothing}
```

Read a GIF image from the byte array.  Returns `nothing` on error.

**Arguments:**

| T   | Name | Default | Description                                |
|:--- |:---- |:------- |:------------------------------------------ |
| R   | data |         | The byte array to read the GIF image from. |
