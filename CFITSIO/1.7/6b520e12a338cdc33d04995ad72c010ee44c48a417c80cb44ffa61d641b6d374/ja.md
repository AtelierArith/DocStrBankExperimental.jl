```
fits_movrel_hdu(f::FITSFile, hduNum::Integer)
```

現在のHDUを`hduNum`HDUだけ前方または後方に移動し（正の値は前方を意味します）、[`fits_movabs_hdu`](@ref)と同じものを返します。
