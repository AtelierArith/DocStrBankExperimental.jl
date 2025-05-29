```
pix_write_jpeg(
    pix::Pix;
    quality::Integer = Int32(75),
    progressive::Bool = false
)::Bool
```

Write an image to a byte array in the JPEG image format.  If there is an error `nothing` is returned.

**Arguments:**

| T   | Name        | Default     | Description                                        |
|:--- |:----------- |:----------- |:-------------------------------------------------- |
| R   | pix         |             | The image to write to a byte array.                |
| O   | quality     | `Int32(75)` | The quality to encode the image at.                |
| O   | progressive | `false`     | Should the progressive encoding algorithm be used? |

**Restriction:**

  * `quality` - Must be in the range 1 to 100.
