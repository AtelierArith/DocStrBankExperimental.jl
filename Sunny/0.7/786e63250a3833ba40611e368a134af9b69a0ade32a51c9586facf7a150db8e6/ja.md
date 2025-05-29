```
set_dipoles_from_mcif!(sys::System, filename::AbstractString)
```

mCIFファイルに従って磁気スーパーセルをロードします。システム`sys`は、正しいスーパーセルの寸法にすでにリサイズされている必要があります。
