```
pix_write_jp2k(
    stream::IO,
    pix::Pix;
    quality::Integer = Int32(34),
    levels::Integer= Int32(5)
)::Bool
```

Write an image to an IO stream in the JP2K image format.  If there is an error `false` is returned.

**Arguments:**

| T   | Name    | Default     | Description                                                    |
|:--- |:------- |:----------- |:-------------------------------------------------------------- |
| R   | stream  |             | The stream to write the image to.                              |
| R   | pix     |             | The image to write to the stream.                              |
| O   | quality | `Int32(34)` | The quality to encode the image at.                            |
| O   | levels  | `Int32(5)`  | The number of reduced resolution images to encode in the file. |

**Restriction:**

  * `quality` - Must be in the range `1` to `100`.
  * `levels` - Can be a value from `1` to `10`.

**Details:**

Setting `quality` to `100` would generate a lossless image.

If levels is `1` then only a full resolution image is encoded in the file.  A value of `2` would cause a full resolution image and half resolution image to be encoded.  The default value of `5` will cause images with a reduction factor of 1, 2, 4, 8, and 16 to be encoded in the file.

Leptonica restricts he number of levels to less than or equal to 10.  However imperical tests show that any value over 8 fails in the OpenJpeg library.
