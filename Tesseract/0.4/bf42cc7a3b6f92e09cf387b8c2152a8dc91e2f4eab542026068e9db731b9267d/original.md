```
pix_read(
    filename::AbstractString;
    jpgLuminance::Bool = false,
    jpgFailOnBadData::Bool = false
)::Union{Pix, Nothing}
```

Load an image from from disk of an unspecified type.  Returns `nothing` if the file could not be loaded.

**Arguments:**

| T   | Name             | Default | Description                                                |
|:--- |:---------------- |:------- |:---------------------------------------------------------- |
| R   | filename         |         | The filename of the image to load.                         |
| O   | jpgLuminance     | `false` | If the image is a JPEG should we only load luminance data? |
| O   | jpgFailOnBadData | `false` | If the image is a JPEG should we ignore bit errors?        |

**Details:**

The two optional parameters are obviously ignored if the image is not a JPEG.
