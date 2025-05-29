```
LPCMZstFormat(lpcm::LPCMFormat; level=3)
LPCMZstFormat(info; level=3)
```

Return a `LPCMZstFormat<:AbstractLPCMFormat` instance that corresponds to Onda's default interleaved LPCM format compressed by `zstd`. This format is assumed for sample data files with the "lpcm.zst" extension.

The `level` keyword argument sets the same compression level parameter as the corresponding flag documented by the `zstd` command line utility.

See https://facebook.github.io/zstd/ for details about `zstd`.
