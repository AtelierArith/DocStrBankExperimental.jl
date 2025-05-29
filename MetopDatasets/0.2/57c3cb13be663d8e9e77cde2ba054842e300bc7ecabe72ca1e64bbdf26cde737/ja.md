```
scale_iasi_spectrum(spec_raw, giadr::GIADR_IASI_XXX_1C; high_precision = false)
scale_iasi_spectrum(spec_raw, giadr::GIADR_IASI_XXX_1C, channel_range::OrdinalRange; high_precision = false)
```

giadrレコード情報を使用してIASI L1Cスペクトルをスケーリングします。`channel_range`は、生のスペクトルのサブセットのみが関数に渡される場合に必要です。`high_precision=true`を設定すると、`Float32`の代わりに`Float64`に変換されます。`ds["gs1cspect"]`の最後の部分にはスケールファクターがないことに注意してください。ここでは、スペクトルは単に`0.0`で埋められています。

# 例

```julia-repl
julia> file_path = "test/testData/IASI_xxx_1C_M01_20240819103856Z_20240819104152Z_N_C_20240819112911Z"
julia> ds = MetopDataset(file_path, auto_convert = false);
julia> giadr = MetopDatasets.read_first_record(ds, MetopDatasets.GIADR_IASI_XXX_1C_V11)
julia> # フルスペクトルをスケーリングします。
julia> scaled_spectrum = MetopDatasets.scale_iasi_spectrum(ds["gs1cspect"], giadr)
julia> # スペクトルのサブセットをスケーリングします。
julia> scaled_spectrum_subset = MetopDatasets.scale_iasi_spectrum(ds["gs1cspect"][10:20,:,:,:], giadr, 10:20)
```
