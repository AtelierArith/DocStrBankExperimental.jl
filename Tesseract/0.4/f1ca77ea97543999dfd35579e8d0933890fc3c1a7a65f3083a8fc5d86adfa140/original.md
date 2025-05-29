```
pix_write_webp(
    filename::AbstractString,
    pix::Pix;
    quality::Integer = Int32(80),
    lossless::Bool = true
)::Bool
```

Write an image to a file in the WEBP image format.  If there is an error `false` is returned.

**Arguments:**

| T   | Name     | Default     | Description                            |
|:--- |:-------- |:----------- |:-------------------------------------- |
| r   | filename |             | The name of the file to write to.      |
| R   | pix      |             | The image to write to disk.            |
| O   | quality  | `Int32(80)` | The quality to encode the image at.    |
| O   | lossless | `false`     | Should the lossless algorithm be used? |

**Restrictions:**

  * `quality` - Must be in the range `1` to `100`.

**Details:**

If the file exists it will be overwritten.

If lossless is set to true then the quality is ignored.
