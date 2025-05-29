```
function TiledWindowView(data::AbstractArray{T,M}, tile_size::NTuple{M,Int};
                         rel_overlap::NTuple{M,Float64}=tile_size .*0 .+ 1.0,
                         window_function=window_hanning, get_norm=false, verbose=false, offset=CtrFT) where {T, M}
```

Creates an 2N dimensional view of the data by tiling the N-dimensional data as  specified by tile*size, tile*overlap and optionally tile*center. Additionally a window is applied to this view. If the window*type as defined in IndexFunArrays sums up to one, which is the case for window*linear and window*hanning, a linear decomposition of the data is obtained apart from possible border effects. `data`. the inputdata to decompose into a TiledView. No copies are made for the TiledView and the raw data can be accessed via myview.parent.

`tile_size`. A Tuple describing the size of each tile. This size will form the first N dimensions of the result of size(myview). The second N dimensions refer to N-dimensional tile numbering.

`rel_overlap`. Tuple specifying the relative overlap between successive tiles. The absolute overlap is then calculated as `round.(Int,tile_size./2.0 .* rel_overlap)`.

`window_function`. The window function as defined in IndexFunArrays to apply to the TiledView. The result is currently not any longer a view as it is unclear how to wrap the multiplication into a view. For this reason the TiledView without the window applied is also returned and can be used for assignments. By default a von Hann window (window_hanning) is used.

`get_norm`. An optional Boolean argument allowing to also obtain the normalization map for the boarder pixels, which not necessarily undergo all required window operations. In a future version it may be possible to automatically lay out the windowing such that this effect can be avoided.

`verbose`. If true, diagnostic information on the window layout is printed.

`offset`. defines where the center of the window is placed. See `IndexFunArrays.jl` for details.

# Returns

myview, matching*window = TiledWindowView ... a Tuple of two or three (get*norm=true) with

`myview`. the TiledView of the data without the window which can also be written to.

`matching_window`. a window that can be applied to the view via multiplication myview.*matching_window This is intentionally not provided as a product to separate the features conceptually when it comes to write access.

`normalized`. only returned for get_norm=true. Contains an array with the normalization information by mapping the window back to the original data. This is useful for incomplete coverage of the tiles  as well as using windows which do not sum up to one in the tiling process.

Note that it may be dangerous to directly access the view via a simple .+= operation as it is not entirely clear, whether it is always garanteed that there could not be any running conditions with read-write operations, since some points in the referenced array are accessed multiple times. To avoid such an effect, you can, for example, only acess every second tile along each dimension in one call.

# Examples

```jldoctest
julia> data = ones(10,10).+0.0;

julia> myview, matching_window = TiledWindowView(data, (5, 5); verbose=true);
[ Info: Tiles with pitch (3, 3) overlap by (2, 2) pixels.
[ Info: Window starts at (0.5, 0.5) and ends at (2.5, 2.5).

julia> size(myview)
(5, 5, 5, 5)

julia> matching_window
5×5 IndexFunArrays.IndexFunArray{Float64, 2, IndexFunArrays.var"#360#362"{Float64, Tuple{Int64, Int64}, Tuple{Int64, Int64}, Tuple{Float64, Float64}, Tuple{Float64, Float64}}}:
 0.0214466  0.125     0.146447  0.125     0.0214466
 0.125      0.728553  0.853553  0.728553  0.125
 0.146447   0.853553  1.0       0.853553  0.146447
 0.125      0.728553  0.853553  0.728553  0.125
 0.0214466  0.125     0.146447  0.125     0.0214466

julia> windowed = collect(myview .* matching_window);

julia> myview[:,:,:,:].=0;  # cleares the original array

julia> myview.parent
10×10 Matrix{Float64}:
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0

julia> myview .+= windowed;  # writes the windowed data back into the array

julia> data # lets see if the weigths correctly sum to one?
10×10 Matrix{Float64}:
 1.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0
 1.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0
 1.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0
 1.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0
 1.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0
 1.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0
 1.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0
 1.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0
 1.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0
 1.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0  1.0

julia> # This result may also be used for subsequent normalization but can also be directly obtained by
 
julia> myview, matching_window, normalized = TiledWindowView(rand(10,10).+0, (5, 5); get_norm=true);
```
