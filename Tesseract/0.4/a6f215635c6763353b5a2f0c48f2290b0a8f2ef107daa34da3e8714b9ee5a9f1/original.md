```
pix_read_jpeg(
    data::AbstractArray{UInt8};
    cmap::Bool = false,
    reduction::Integer = Int32(1),
    luminance::Bool = false,
    ignoreErrors::Bool = false
)::Union{Pix, Nothing}
```

Read a JPEG image from the byte array.  Returns `nothing` on error.

**Arguments:**

| T   | Name         | Default    | Description                                 |
|:--- |:------------ |:---------- |:------------------------------------------- |
| R   | data         |            | The byte array to read the JPEG image from. |
| O   | cmap         | `false`    | Load the image as color mapped.             |
| O   | reduction    | `Int32(1)` | Load a reduced resolution image.            |
| O   | luminance    | `false`    | Only load the luminace data from the image. |
| O   | ignoreErrors | `false`    | Ignore errors in the file.                  |

**Restrictions:**

  * `cmap` - Requires that SPP be 3 or 4 in the image, so not all JPEG images can be loaded as          color mapped.
  * `reduction` - Must be 1, 2, 4, or 8.

**Details:**

The `reduction` parameter can be used to load the image faster but at a reduced resolution.  The JPEG specifification allows the reader to recover from bit errors. Setting `ignoreErrors` to true will allow files with bit errors to be loaded but the image may not be correct.
