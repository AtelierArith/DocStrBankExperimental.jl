```
newadd, me = get_offdiagonal(ham, address, chosen)
```

ハミルトニアン `ham` の単一の（オフダイアゴナル）行列要素の値 `me` と新しいアドレス `newadd` を計算します。オフダイアゴナル要素はアドレス `address` と同じ列にあり、整数インデックス `chosen` によってインデックス付けされています。

# 例

```jldoctest
julia> addr = BoseFS(3, 2, 1);

julia> H = HubbardMom1D(addr);

julia> get_offdiagonal(H, addr, 3)
(BoseFS{6,3}(2, 1, 3), 1.0)
```

[`AbstractHamiltonian`](@ref) インターフェースの一部です。
