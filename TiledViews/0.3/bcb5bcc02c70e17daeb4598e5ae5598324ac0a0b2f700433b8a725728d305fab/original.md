```
tiled_processing(tiled_view::TiledView, fct; verbose=true, dtype=eltype(tiled_view.parent), window_function=window_hanning)
```

Processes a raw dataset using tiled views by submitting each tile to the function `fct` and merging the results via the `window_function`.

Returns a TiledView of the result. The untiled result can be accessed via `.parent` member.

To be able to handle also functions that habe mutiple return values as a tuple, the accessor function can be used to extract the relevant value from the tuple. The default is the identity function, which is used for functions that return a single value. If a tuple of accessor functions is provided, each accessor function will be called and individual an return array for each element of the tuple is constructed and returned as a tuple.

## Arguments

  * `tiled_view`: the input data to decompose into a TiledView. No copies are made for the TiledView and the raw data can be accessed via `.parent`.
  * `fct`: the function to be applied to each tile. The function should accept a single argument, which is the tile data.
  * `verbose`: If true, diagnostic information on the window layout is printed.
  * `dtype`: The element type of the new array. By default, it is the same as the type of the parent array of `tiled_view`.
  * `window_function`: The window function as defined in IndexFunArrays to apply to the TiledView. The result is currently not any longer a view as it is unclear how to wrap the multiplication into a view. For this reason the TiledView without the window applied is also returned and can be used for assignments. By default a Hanning window (window_hanning) is used.
  * `accessor`: A function to access the data in the tile. By default, it is the identity function.
