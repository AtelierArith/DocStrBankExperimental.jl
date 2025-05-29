```
pix_write_tiff(
    stream::IO,
    pix::Pix;
    compression::IFF = IFF_TIFF
)::Bool
```

Write an image to an IO stream in the TIFF image format. Returns `false` if there was an error.

**Arguments:**

| T   | Name        | Default    | Description                          |
|:--- |:----------- |:---------- |:------------------------------------ |
| R   | stream      |            | The stream to write the image to.    |
| R   | pix         |            | The image to write to disk.          |
| O   | compression | `IFF_TIFF` | The compression to use on the image. |

**Restrictions:**

  * `compression` - Must be a one of the following compression formats:

      * `IFF_TIFF` - Supports all images.
      * `IFF_TIFF_RLE` - Requires a b&w 1bpp image.
      * `IFF_TIFF_PACKBITS` - Requires a b&w 1bpp image.
      * `IFF_TIFF_G3` - Requires a b&w 1bpp image.
      * `IFF_TIFF_G4` - Requires a b&w 1bpp image.
      * `IFF_TIFF_LZW` - Supports all images.
      * `IFF_TIFF_ZIP` - Supports all images.
      * `IFF_TIFF_JPEG` - Supports all images.

**Details:**

The default compression is no compression.
