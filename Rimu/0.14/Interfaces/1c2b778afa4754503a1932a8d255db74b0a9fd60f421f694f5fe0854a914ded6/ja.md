```
num_offdiagonals(ham, address)
```

アドレス `address` から到達可能な構成の数を計算します。

# 例

```jldoctest
julia> address = BoseFS((3, 2, 1));


julia> H = HubbardMom1D(address);


julia> num_offdiagonals(H, address)
10
```

[`AbstractHamiltonian`](@ref) インターフェースの一部です。
