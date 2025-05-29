```
scale_iasi_spectrum(spec_raw, giadr::GIADR_IASI_XXX_1C; high_precision = false)
scale_iasi_spectrum(spec_raw, giadr::GIADR_IASI_XXX_1C, channel_range::OrdinalRange; high_precision = false)
```

Scaling the IASI L1C spectrum using the giadr record information. The `channel_range` is needed if only a  subset of the raw spectrum is passed to the function.  Setting `high_precision=true` will convert to `Float64` instead of `Float32`.  Note that the end part of the  `ds["gs1cspect"]` does not have any scale factors. Here the spectrum is just  filled with `0.0`.

# Example

```julia-repl
julia> file_path = "test/testData/IASI_xxx_1C_M01_20240819103856Z_20240819104152Z_N_C_20240819112911Z"
julia> ds = MetopDataset(file_path, auto_convert = false);
julia> giadr = MetopDatasets.read_first_record(ds, MetopDatasets.GIADR_IASI_XXX_1C_V11)
julia> # Scale full spectrum.
julia> scaled_spectrum = MetopDatasets.scale_iasi_spectrum(ds["gs1cspect"], giadr)
julia> # Scale subset of spectrum.
julia> scaled_spectrum_subset = MetopDatasets.scale_iasi_spectrum(ds["gs1cspect"][10:20,:,:,:], giadr, 10:20)
```
