```
sample(raster, [sink]; fraction=0.1)
```

Randomly sample a percentage of non-missing values from the provided raster.

# Parameters

  * `raster`: The `AbstractRaster` or `AbstractRasterStack` from which to sample.
  * `sink`: A `Tables.jl` materializer (default =`Tables.columntable`).
  * `fraction`: The fraction of values to sample (default = 10%).

# Example

```julia
julia> src = Landsat8("LC08_L2SP_043024_20200802_20200914_02_T1/");

julia> rs = RasterStack(src, [:blue, :green, :red, :nir]);

julia> sample(rs, DataFrame)
4054017×4 DataFrame
     Row │ B2      B3      B4      B5     
         │ UInt16  UInt16  UInt16  UInt16 
─────────┼────────────────────────────────
       1 │   7841    9082    8174   24372
       2 │   8117    8977    8372   15577
       3 │  26460   26601   26579   27023
    ⋮    │   ⋮       ⋮       ⋮       ⋮
 4054015 │   7735    8403    7929   18386
 4054016 │   6984    9559   10026   11986
 4054017 │   8036    8658    8328   13896
                      4054011 rows omitted
```
