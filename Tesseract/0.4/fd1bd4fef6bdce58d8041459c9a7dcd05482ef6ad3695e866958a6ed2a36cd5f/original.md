```
pix_write_png(
    stream::IO,
    pix::Pix
    gamma::AbstractFloat = Float32(0.0)
)::Bool
```

Write an image to a stream in the PNG image format.  If there is an error `false` is returned.

**Arguments:**

| T   | Name   | Default        | Description                             |
|:--- |:------ |:-------------- |:--------------------------------------- |
| R   | stream |                | The stream to write the data to.        |
| R   | pix    |                | The image to write to the stream.       |
| O   | gamma  | `Float32(0.0)` | The gamma value to write to the header. |

**Restrictions:**

  * `gamma` - Must be in the range 0.0 to 1.0 inclusively.

**Details:**

If gamma is set to `0.0` then no gamma value will be written in the image header.
