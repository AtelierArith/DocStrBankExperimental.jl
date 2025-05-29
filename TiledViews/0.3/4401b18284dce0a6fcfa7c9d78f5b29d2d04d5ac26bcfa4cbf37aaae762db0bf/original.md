```
get_window(A::TiledView; window_function=window_hanning, get_norm=false, verbose=false, offset = CtrFT);
```

Calculates a window matching to the `TiledView`.

`window_function`. The window function as defined in IndexFunArrays to apply to the TiledView. The result is currently not any longer a view as it is unclear how to wrap the multiplication into a view. For this reason the TiledView without the window applied is also returned and can be used for assignments. By default a von Hann window (window_hanning) is used. For even sizes the window is centered at the integer coordinate right of the middle position (`CtrFT`).

`get_norm`. An optional Boolean argument allowing to also obtain the normalization map for the boarder pixels, which not necessarily undergo all required window operations. In a future version it may be possible to automatically lay out the windowing such that this effect can be avoided.

`verbose`. If true, diagnostic information on the window layout is printed.

`offset`. defines where the center of the window is placed. See `IndexFunArrays.jl` for details.

# Returns

`matching_window`. a window that can be applied to the view via multiplication myview.*matching_window This is intentionally not provided as a product to separate the features conceptually when it comes to write access.

`normalized`. only returned for get_norm=true. Contains an array with the normalization information by mapping the window back to the original data. This is useful for incomplete coverage of the tiles  as well as using windows which do not sum up to one in the tiling process.

# Examples

```jldoctest
julia> data = ones(10,10).+0.0;

julia> myview = TiledView(data, (5, 5), (2,2));

julia> win = get_window(myview, verbose=true);
[ Info: Tiles with pitch (3, 3) overlap by (2, 2) pixels.
[ Info: Window starts at (0.5, 0.5) and ends at (2.5, 2.5).

julia> win
5×5 IndexFunArrays.IndexFunArray{Float64, 2, IndexFunArrays.var"#360#362"{Float64, Tuple{Int64, Int64}, Tuple{Int64, Int64}, Tuple{Float64, Float64}, Tuple{Float64, Float64}}}:
 0.0214466  0.125     0.146447  0.125     0.0214466
 0.125      0.728553  0.853553  0.728553  0.125
 0.146447   0.853553  1.0       0.853553  0.146447
 0.125      0.728553  0.853553  0.728553  0.125
 0.0214466  0.125     0.146447  0.125     0.0214466

```

see TiledWindowView() for more examples.
