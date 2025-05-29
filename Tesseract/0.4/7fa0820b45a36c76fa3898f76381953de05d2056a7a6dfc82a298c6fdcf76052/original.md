```
pix_write_tiff(
    filename::AbstractString,
    pix::Pix;
    compression::IFF = IFF_TIFF,
    append::Bool = false
)::Bool
```

Write an image to a file in the TIFF image format. Returns `false` if there was an error.

**Arguments:**

| T   | Name        | Default    | Description                                             |
|:--- |:----------- |:---------- |:------------------------------------------------------- |
| R   | filename    |            | The name of the file to write to or create.             |
| R   | pix         |            | The image to write to disk.                             |
| O   | compression | `IFF_TIFF` | The compression to use on the image.                    |
| O   | append      | `false`    | Should we overwrite the image or append it to the file. |

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

TIFF files can contain multiple image.  If a file does not exist it will be created.  If the file exists and append is `false` then the file will be overwritten.  If append is `true` then the image will be added to the file.
