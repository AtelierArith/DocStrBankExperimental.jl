```
mri_spectra(fx, fy, oa::Array{<:Object2d}, fit::NamedTuple)
```

`spectrum`のバージョンで、以前に`mri_smap_fit`を使用してフィットされた感度マップを持つ並列MRIに適しています。`length(fx)`の次元を持つ`ncoil`のk空間データベクトルのベクトルを返します。
