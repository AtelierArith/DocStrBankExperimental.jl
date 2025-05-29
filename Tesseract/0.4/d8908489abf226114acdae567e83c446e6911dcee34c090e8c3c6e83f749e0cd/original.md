```
pix_read_tiff(
    stream::IO;
    page::Integer = Int32(1)
)::Union{Pix, Nothing}
```

Read a TIFF image from the specified stream.  Returns `nothing` on error.

**Arguments:**

| T   | Name   | Default    | Description                               |
|:--- |:------ |:---------- |:----------------------------------------- |
| R   | stream |            | The IO stream to read the TIFF file from. |
| O   | page   | `Int32(1)` | The image to load from the file.          |

**Restrictions:**

  * `page` - Must be greater than 0.

**Details:**

This implementation mirrors the API provided by Leptonica when you pass in a FILE pointer. This assumes that the remainder of the stream contains a TIFF image.

TIFF files can contain multiple images.  The `page` parameter allows you to specify which image you want to load.
