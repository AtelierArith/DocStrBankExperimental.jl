```
pix_write_jpeg(
    filename::AbstractString,
    pix::Pix;
    quality::Integer = Int32(75),
    progressive::Bool = false
)::Bool
```

Write an image to a file in the JPEG image format.  If there is an error `false` is returned.

**Arguments:**

| T   | Name        | Default     | Description                                        |
|:--- |:----------- |:----------- |:-------------------------------------------------- |
| R   | filename    |             | The name of the file to write to.                  |
| R   | pix         |             | The image to write to the file.                    |
| O   | quality     | `Int32(75)` | The quality to encode the image at.                |
| O   | progressive | `false`     | Should the progressive encoding algorithm be used? |

**Restriction:**

  * `quality` - Must be in the range 1 to 100.

**Details:**

If the file exists it will be overwritten.
