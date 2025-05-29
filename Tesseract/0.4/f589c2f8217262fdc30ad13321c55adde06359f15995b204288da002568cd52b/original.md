```
pix_write_png(
    pix::Pix
    gamma::AbstractFloat = Float32(0.0)
)::Union{Vector{UInt8}, Nothing}
```

Write an image to a byte array in the PNG image format.  If there is an error `false` is returned.

**Arguments:**

| T   | Name  | Default        | Description                             |
|:--- |:----- |:-------------- |:--------------------------------------- |
| R   | pix   |                | The image to write to a byte array.     |
| O   | gamma | `Float32(0.0)` | The gamma value to write to the header. |

**Restrictions:**

  * `gamma` - Must be in the range 0.0 to 1.0 inclusively.

**Details:**

If gamma is set to `0.0` then no gamma value will be written in the image header.
