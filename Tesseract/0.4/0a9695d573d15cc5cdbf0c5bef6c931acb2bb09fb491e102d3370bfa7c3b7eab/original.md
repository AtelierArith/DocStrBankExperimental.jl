```
pix_read_jp2k(
    stream::IO;
    reduction::Integer = Int32(1),
    box::Union{PixBox, Nothing} = nothing
)::Union{Pix, Nothing}
```

Read a JP2K image from the specified stream.  Returns `nothing` on error.

**Arguments:**

| T   | Name      | Default    | Description                                        |
|:--- |:--------- |:---------- |:-------------------------------------------------- |
| R   | stream    |            | The IO stream to read the JP2K file from.          |
| O   | reduction | `Int32(1)` | Load a reduced version of the image from the file. |
| O   | box       | `nothing`  | Specifies a region to extract from the image.      |

**Restrictions:**

  * `reduction` - Must be a factor of 2.

**Details:**

This implementation mirrors the API provided by Leptonica when you pass in a FILE pointer. This assumes that the remainder of the stream contains a JP2K image.
