```julia
mutable struct LazyBufferedTIFF{T<:Union{ColorTypes.Colorant, TiffImages.WidePixel}, O<:Unsigned, AA<:AbstractArray} <: TiffImages.AbstractDenseTIFF{T<:Union{ColorTypes.Colorant, TiffImages.WidePixel}, 3}
```

A type to represent lazily-loaded TIFF data, returned by `TiffImages.load(filepath; lazyio=true)`. Useful for opening and operating on images too large to store in memory, and for incrementally writing new TIFF files.

This works by buffering individual slices. This allows broad format support, including compressed TIFFs, but with mixed performance depending on your specific access (indexing) patterns. See discussion in the package documentation, and [`MmappedTIFF`](@ref) for an alternative with different strengths and weaknesses.

```jldoctest
julia> using TiffImages, ColorTypes

julia> img = empty(LazyBufferedTIFF, Gray{Float32}, joinpath(mktempdir(), "test.tif"))
32-bit LazyBufferedTIFF{Gray{Float32}} 0×0×0 (writable)
    Current file size on disk:   8 bytes
    Addressable space remaining: 4.000 GiB

julia> close(img) # when you're done, close the stream
```

  * `file`: Pointer to keep track of the backing file

  * `ifds`: The associated tags for each slice in this array

  * `dims`
  * `working_cache`: An internal cache to fill reading from disk

  * `cache`: An internal cache to fill with fully transformed data

  * `cache_index`: The index of the currently loaded slice

  * `last_ifd_offset`: Position of last loaded IFD, updated whenever a slice is appended

  * `readonly`: A flag tracking whether this file is editable
