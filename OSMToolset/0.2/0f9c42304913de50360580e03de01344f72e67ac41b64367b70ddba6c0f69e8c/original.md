```
tile_osm_file(filename::AbstractString, [bounds::Bounds]; nrow::Integer, ncol::Integer, [out_dir::AbstractString]
```

Provide the tiling functionality for maps. A `filename` will be open for processing and the tiling will be done around given `bounds`. If `bounds` are not given they will be calculated using `getbounds` function. The tiling will be performed with a matrix having `nrow` rows and `ncol` columns. The output will be written to the folder name `out_dir`. If none `out_dir` is given than as the output is written to where `filename` is located.

Returns a `Matrix{String}` of size `nrow` x `ncol` containing the names of the files created.
