```
pix_write(
    pix::Pix,
    format::IFF = IFF_DEFAULT
):::Union{Vector{UInt8}, Nothing}
```

Write an image to a byte array in the specified format.  If there is an error `nothing` is returned.

**Arguments:**

| T   | Name   | Default       | Description                                 |
|:--- |:------ |:------------- |:------------------------------------------- |
| R   | pix    |               | The image to write to the stream.           |
| O   | format | `IFF_DEFAULT` | The image format to write the image out as. |

**Details:**

If format isn't specified Leptonica will choose the correct format to write the image as based on the input format.
