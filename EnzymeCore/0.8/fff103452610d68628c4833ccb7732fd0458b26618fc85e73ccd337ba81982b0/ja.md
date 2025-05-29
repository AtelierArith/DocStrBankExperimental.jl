```
struct FFIABI <: ABI
```

外部関数呼び出し [`ABI`](@ref)。微分された関数をJITコンパイルし、その後inttoptrでアドレスを呼び出します。
