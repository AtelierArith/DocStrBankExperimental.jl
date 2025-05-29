```
access!(pool::CuMemoryPool, dev::CuDevice, flags::CUmemAccess_flags)
access!(pool::CuMemoryPool, devs::Vector{CuDevice}, flags::CUmemAccess_flags)
```

デバイス `dev` またはデバイスのリスト `devs` に対するメモリプール `pool` の可視性を制御します。
