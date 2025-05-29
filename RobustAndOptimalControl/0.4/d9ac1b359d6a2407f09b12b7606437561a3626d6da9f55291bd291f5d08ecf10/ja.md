```
feedback(sys1::ExtendedStateSpace, sys2::ExtendedStateSpace;
    W1 = 1:sys1.nw,
    U1 = (1:sys1.nu) .+ sys1.nw,
    Z1 = 1:sys1.nz,
    Y1 = (1:sys1.ny) .+ sys1.nz,
    W2 = 1:sys2.nw,
    U2 = (1:sys2.nu) .+ sys2.nw,
    Z2 = 1:sys2.nz,
    Y2 = (1:sys2.ny) .+ sys2.nz,
    kwargs...)
```

[`ExtendedStateSpace`](@ref) システムは、入力と出力の分割に基づいてデフォルトのフィードバックインデックスを使用します。
