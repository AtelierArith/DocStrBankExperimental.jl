```
pix_read_tiff(
    filename::AbstractString;
    page::Integer = Int32(1)
)::Union{Pix, Nothing}
```

Read a TIFF image from the specified file.  Returns `nothing` on error.

**Arguments:**

| T   | Name     | Default    | Description                        |
|:--- |:-------- |:---------- |:---------------------------------- |
| R   | filename |            | The name of the TIFF file to load. |
| O   | page     | `Int32(1)` | The image to load from the file.   |

**Restrictions:**

  * `page` - Must be greater than 0.

**Details:**

TIFF files can contain multiple images.  The `page` parameter allows you to specify which image you want to load.
