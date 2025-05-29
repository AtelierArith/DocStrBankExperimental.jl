```
starting_address(h)
```

ハミルトニアン `h` の開始アドレスを返します。`AbstractMatrix` に対して呼び出すと、`starting_address` は最も低い対角要素のインデックスを返します。

# 例

```jldoctest
julia> address = BoseFS((3, 2, 1));


julia> H = HubbardMom1D(address);


julia> address == starting_address(H)
true
```

[`AbstractHamiltonian`](@ref) インターフェースの一部です。
