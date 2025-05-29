```
shift_lattice(is)
```

区間 `[M÷2, M÷2)` 内の連続インデックス `is` を円形にシフトし、セットが 0 から始まるようにします。ここで、`M=length(is)` です。

逆操作: [`shift_lattice_inv`](@ref)。[`HubbardReal1DEP`](@ref) および [`HubbardMom1DEP`](@ref) で使用されます。
