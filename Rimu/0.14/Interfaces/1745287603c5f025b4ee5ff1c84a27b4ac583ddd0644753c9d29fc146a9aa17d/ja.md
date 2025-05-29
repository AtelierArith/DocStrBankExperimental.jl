```
diagonal_element(ham, address)
```

線形演算子 `ham` の対角行列要素をアドレス `address` で計算します。

# 例

```jldoctest
julia> address = BoseFS((3, 2, 1));


julia> H = HubbardMom1D(address);


julia> diagonal_element(H, address)
8.666666666666664
```

[`AbstractHamiltonian`](@ref) インターフェースの一部です。
