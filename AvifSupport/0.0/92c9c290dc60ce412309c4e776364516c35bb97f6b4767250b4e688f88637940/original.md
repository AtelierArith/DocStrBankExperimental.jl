```
avif_encode(image::AbstractMatrix{TColor}) -> Vector{UInt8}
avif_encode(image_arr::AbstractArray) -> Vector{UInt8}
```

Encode 2D image `img`or an array of 2D images `image_arr` as an AVIF byte sequence . The return value is a vector of bytes.

# Parameters for avif_encode(image::AbstractMatrix{TColor})

  * `transpose::Bool`: whether we need to permute the image's width and height dimension

before encoding. The default value is `false`.

  * `quality::Int`: The quality value is between 0..100 . The default value is `10`.

      * `transpose::Bool`: whether we need to permute the image's width and height dimension

    before encoding. The default value is `false`.
  * `mode::String`: Determines the type of encoding of the input image .For 2D images ,  the encoding mode is one of two values : "one_frame" which is the default and "grid".

    # Parameters for avif*encode(image*arr::AbstractArray)

      * `transpose::Bool`: whether we need to permute the image's width and height dimension

    before encoding. The default value is `false`.

      * `quality::Int`: The quality value is between 0..100 . The

    default value is `10`.

      * `mode::String`: Determines the type of encoding of the input .For arrays of 2D images ,

    the encoding mode is one of three values : `"seq"` (for sequential) which is the default , `"grid"` or `"layered"` .

      * `grid_cols::Int`: - ONLY RELEVANT TO GRID ENCODING - Determines the number of columns of the resulting image .

    The grid_cols value depends on the length of the input vector.  The default value is `1`.

      * `grid_rows::Int`: - ONLY RELEVANT TO GRID ENCODING - Determines the number of rows of the resulting image .

    The grid_rows value depends on the length of the input vector. The default value is `1`.

      * `timescale::Int`: - ONLY RELEVANT TO LAYERED ENCODING -

    default value is `1`.

!!! info "Custom Encoding parameters"
    LibAvif has a large number of encoder parameters that determine how the image is encoded. Most applications don't need or want to know about all these parameters. For more detailed information and explaination, please refer to the document [1].  Unsupported custom parameters might cause Julia segmentation fault.

    The following are the default parameters used in this implementation for decoding :

      * codecChoice = libaom
      * maxThreads = Threads.nthreads()
      * speed = 4


!!! danger "For Grid Encoding"
    ```
    grid_cols * grid_rows = length(image_arr)
    ```


# References

  * [1] [libavif avifenc.c ](https://github.com/AOMediaCodec/libavif/blob/main/apps/avifenc.c)
