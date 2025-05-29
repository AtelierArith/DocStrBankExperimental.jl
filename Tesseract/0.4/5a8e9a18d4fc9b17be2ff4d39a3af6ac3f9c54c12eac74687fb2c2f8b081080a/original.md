```
pix_read_bmp(
    data::AbstractArray{UInt8}
)::Union{Pix, Nothing}
```

Read a BMP image from the byte array.  Returns `nothing` on error.

**Arguments:**

| T   | Name | Default | Description                                |
|:--- |:---- |:------- |:------------------------------------------ |
| R   | data |         | The byte array to read the BMP image from. |
