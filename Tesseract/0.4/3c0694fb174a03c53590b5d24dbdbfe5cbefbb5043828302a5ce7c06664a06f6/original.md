```
pix_write(
    filename::String,
    pix::Pix,
    format::IFF = IFF_DEFAULT
)::Bool
```

Write an image to disk in the specified format.  If there is an error `false` is returned.

**Arguments:**

| T   | Name     | Default       | Description                                 |
|:--- |:-------- |:------------- |:------------------------------------------- |
| R   | filename |               | The filename to write the image to.         |
| R   | pix      |               | The image to write to disk.                 |
| O   | format   | `IFF_DEFAULT` | The image format to write the image out as. |

**Details:**

If the file exists it will be overwritten.

If format isn't specified Leptonica will choose the correct format to write the image as based on the input format.
