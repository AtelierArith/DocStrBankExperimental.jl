```
unsafe_adler32(data, start=UInt32(1))::UInt32
```

ポインタ `in_ptr` の最初の `n_in` の adler32 チェックサムを、シード `start`（デフォルトは 1）で計算します。

参照: [`adler32`](@ref)
