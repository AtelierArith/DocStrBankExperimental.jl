```
pix_write_webp(
    stream::IO,
    pix::Pix;
    quality::Integer = Int32(80),
    lossless::Bool = true
)::Bool
```

Write an image to a stream in the WEBP image format.  If there is an error `false` is returned.

**Arguments:**

| T   | Name     | Default     | Description                            |
|:--- |:-------- |:----------- |:-------------------------------------- |
| R   | stream   |             | The IO stream to write to.             |
| R   | pix      |             | The image to write to the stream.      |
| O   | quality  | `Int32(80)` | The quality to encode the image at.    |
| O   | lossless | `false`     | Should the lossless algorithm be used? |

**Restrictions:**

  * `quality` - Must be in the range `1` to `100`.

**Details:**

If the file exists it will be overwritten.

If lossless is set to true then the quality is ignored.
