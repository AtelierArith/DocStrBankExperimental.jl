```
pix_write_jpeg(
    stream::IO,
    pix::Pix;
    quality::Integer = Int32(75),
    progressive::Bool = false
)::Bool
```

Write an image to an IO stream in the JPEG image format.  If there is an error `false` is returned.

**Arguments:**

| T   | Name        | Default     | Description                                        |
|:--- |:----------- |:----------- |:-------------------------------------------------- |
| R   | stream      |             | The stream to write the image to.                  |
| R   | pix         |             | The image to write to the stream.                  |
| O   | quality     | `Int32(75)` | The quality to encode the image at.                |
| O   | progressive | `false`     | Should the progressive encoding algorithm be used? |

**Restriction:**

  * `quality` - Must be in the range 1 to 100.
