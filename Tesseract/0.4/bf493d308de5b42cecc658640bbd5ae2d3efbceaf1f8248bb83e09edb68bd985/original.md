```
pix_read_webp(
    data::AbstractArray{UInt8}
)::Union{Pix, Nothing}
```

Read a WEBP image from the byte array.  Returns `nothing` on error.

**Arguments:**

| T   | Name | Default | Description                                 |
|:--- |:---- |:------- |:------------------------------------------- |
| R   | data |         | The byte array to read the WEBP image from. |
