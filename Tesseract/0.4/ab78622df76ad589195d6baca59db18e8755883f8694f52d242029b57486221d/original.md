```
pix_read_jpeg(
    stream::IO;
    cmap::Bool = false,
    reduction::Integer = Int32(1),
    luminance::Bool = false,
    ignoreErrors::Bool = false
)::Union{Pix, Nothing}
```

Read a JPEG image from the specified stream.  Returns `nothing` on error.

**Arguments:**

| T   | Name         | Default    | Description                                 |
|:--- |:------------ |:---------- |:------------------------------------------- |
| R   | stream       |            | The IO stream to read the JPEG file from.   |
| O   | cmap         | `false`    | Load the image as color mapped.             |
| O   | reduction    | `Int32(1)` | Load a reduced resolution image.            |
| O   | luminance    | `false`    | Only load the luminace data from the image. |
| O   | ignoreErrors | `false`    | Ignore errors in the file.                  |

**Restrictions:**

  * `cmap` - Requires that SPP be 3 or 4 in the image, so not all JPEG images can be loaded as          color mapped.
  * `reduction` - Must be 1, 2, 4, or 8.

**Details:**

This implementation mirrors the API provided by Leptonica when you pass in a FILE pointer. This assumes that the remainder of the stream contains a JPEG image.

The `reduction` parameter can be used to load the image faster but at a reduced resolution.  The JPEG specifification allows the reader to recover from bit errors. Setting `ignoreErrors` to true will allow files with bit errors to be loaded but the image may not be correct.
