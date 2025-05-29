```
pad_zeros(x, pad::Tuple; [dims])
pad_zeros(x, pad::Int; [dims])
```

配列 `x` をゼロでパディングします。定数が 0 に等しい [`pad_constant`](@ref) と同等です。
