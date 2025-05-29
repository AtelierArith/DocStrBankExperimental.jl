```
tiled_processing(data, fct, tile_size, tile_overlap = tile_size .* 0; verbose=true, dtype=eltype(data), keep_center=false, window_function=nothing)
```

Processes a raw dataset using tiled views by wrapping the `data` in a TiledView, and submitting each tile to the function `fct` and merging the results via the `window_function`. Returns a TiledView of the result. The untiled result can be accessed via `.parent` member. Note that this version with the `tile_size` adds a view conveniences: If the tile size specifies fewer dimensions than the data, the trailing dimensions are automatically expanded to match the full size of the data.  The default `nothing` in the window*function assures that no window is applied if no overlap is used. With overlap this changes automatically to a Hanning window. Furthermore, as opposed to the other version, the keep*center option has the default value of false, which is more convenient for most applications that just tile arrays in a matching way.

If the first processed tile returns an array with a size that is neither equal to the input tile size or a projection thereof, the result is a tuple of arrays of the same size as the input tile size, an array of arrays one for each tile is returned.

## Arguments

  * `data`: the input data to decompose into a TiledView. No copies are made for the TiledView and the raw data can be accessed via `.parent`.
  * `fct`: the function to be applied to each tile. The function should accept a single argument, which is the tile data.
  * `tile_size`: A Tuple describing the size of each tile. This size will form the first N dimensions of the result of `size(myview)`. The second N dimensions refer to N-dimensional tile numbering.
  * `tile_overlap`: Tuple specifying the overlap between successive tiles in voxels. This implicitely defines the pitch between tiles as `(tile_size .- tile_overlap)`.
  * `verbose`: If true, diagnostic information on the window layout is printed.
  * `dtype`: The element type of the new array. By default, it is the same as the type of the parent array of `data`.
  * `keep_center`: This boolean (default: false) specifies whether the center of the parent `data` will be aligned with the center of the central tile. If `false`, the first tile starts at offset zero.
  * `window_function`: The window function as defined in IndexFunArrays to apply to the TiledView. The result is currently not any longer a view as it is unclear how to wrap the multiplication into a view. For this reason the TiledView without the window applied is also returned and can be used for assignments. By default a Hanning window (window_hanning) is used.

## Example

```jldoctest
julia> res = tiled_processing(ones(10,10), (a)->10*a, (2,2), (0,0), verbose=false).parent
10×10 Matrix{Float64}:
 10.0  10.0  10.0  10.0  10.0  10.0  10.0  10.0  10.0  10.0
 10.0  10.0  10.0  10.0  10.0  10.0  10.0  10.0  10.0  10.0
 10.0  10.0  10.0  10.0  10.0  10.0  10.0  10.0  10.0  10.0
 10.0  10.0  10.0  10.0  10.0  10.0  10.0  10.0  10.0  10.0
 10.0  10.0  10.0  10.0  10.0  10.0  10.0  10.0  10.0  10.0
 10.0  10.0  10.0  10.0  10.0  10.0  10.0  10.0  10.0  10.0
 10.0  10.0  10.0  10.0  10.0  10.0  10.0  10.0  10.0  10.0
 10.0  10.0  10.0  10.0  10.0  10.0  10.0  10.0  10.0  10.0
 10.0  10.0  10.0  10.0  10.0  10.0  10.0  10.0  10.0  10.0
 10.0  10.0  10.0  10.0  10.0  10.0  10.0  10.0  10.0  10.0

julia> tiled_processing(ones(10,20), (a)->sum(a, dims=2), (2,), verbose=false).parent
10×1 Matrix{Float64}:
 20.0
 20.0
 20.0
 20.0
 20.0
 20.0
 20.0
 20.0
 20.0
 20.0

julia> fct = (a)->[3 .*a, sum(a, dims=2), "result: $(sum(a))"]; # a function that returns a tuple of three values of very different types

julia> tiled_processing(ones(5,6), fct, (2,), verbose=false)
3-element Vector{AbstractArray}:
 [3.0 3.0 … 3.0 3.0; 3.0 3.0 … 3.0 3.0;;; 3.0 3.0 … 3.0 3.0; 3.0 3.0 … 3.0 3.0;;; 3.0 3.0 … 3.0 3.0; 0.0 0.0 … 0.0 0.0;;;;]
 [6.0; 6.0;;; 6.0; 6.0;;; 6.0; 0.0;;;;]
 ["result: 12.0"; "result: 12.0"; "result: 6.0";;]
```
