```
unsafe_crc32(in_ptr::Ptr, n_in::Integer, start::UInt32)::UInt32
```

ポインタ `in_ptr` の最初の `n_in` バイトの crc32 チェックサムを、シード `start`（デフォルトは 0）を使用して計算します。crc32 は、Julia 標準ライブラリで提供されている `crc32c` とは異なる、より遅いアルゴリズムであることに注意してください。

参照: [`crc32`](@ref)
