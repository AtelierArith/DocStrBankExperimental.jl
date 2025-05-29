```
avif_decode(filename::Union{AbstractString,IO}; kwargs...) -> Vector{Matrix{Colorant}}
avif_decode(data::Vector{UInt8}; kwargs...) -> Vector{Matrix{Colorant}}
```

Decode the AVIF image as an array of colorant matrices. The source data can be either a filename, an IO , or an in-memory byte sequence.The output is an array of matrices of type `Colorant`.

# parameters

  * `transpose::Bool`: whether we need to permute the image's width and height dimension before encoding. The default value is `false`.

    !!! info "Custom Decoding parameters"



    LibAvif has a large number of decoder parameters that determine how the image is   decoded. Most applications don't need or want to know about all these parameters. For   more detailed information and explaination, please refer to the documents in [1].    Unsupported custom parameters might cause Julia segmentation fault.

    The following are the default parameters used in this implementation for decoding :

      * codecChoice = libaom
      * maxThreads = Threads.nthreads()
      * speed = 4

# References

  * [1] [libavif avifdec.c ](https://github.com/AOMediaCodec/libavif/blob/main/apps/avifdec.c)
