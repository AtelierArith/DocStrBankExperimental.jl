```
pix_read_tiff(
    data::AbstractArray{UInt8};
    page::Integer = Int32(1)
)::Union{Pix, Nothing}
```

Read a TIFF image from the byte array.  Returns `nothing` on error.

**Arguments:**

| T   | Name | Default    | Description                                 |
|:--- |:---- |:---------- |:------------------------------------------- |
| R   | data |            | The byte array to read the TIFF image from. |
| O   | page | `Int32(1)` | The image to load from the file.            |

**Restrictions:**

  * `page` - Must be greater than 0.

**Details:**

TIFF files can contain multiple images.  The `page` parameter allows you to specify which image you want to load.
