```
pix_read_jp2k(
    data::AbstractArray{UInt8};
    reduction::Integer = Int32(1),
    box::Union{PixBox, Nothing} = nothing
)::Union{Pix, Nothing}
```

Read a JP2K image from the byte array.  Returns `nothing` on error.

**Arguments:**

| T   | Name      | Default    | Description                                        |
|:--- |:--------- |:---------- |:-------------------------------------------------- |
| R   | data      |            | The byte array to read the JP2K image from.        |
| O   | reduction | `Int32(1)` | Load a reduced version of the image from the file. |
| O   | box       | `nothing`  | Specifies a region to extract from the image.      |

**Restrictions:**

  * `reduction` - Must be a factor of 2.
