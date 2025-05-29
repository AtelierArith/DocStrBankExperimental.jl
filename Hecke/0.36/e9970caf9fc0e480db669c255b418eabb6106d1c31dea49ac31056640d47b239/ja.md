```
k3_lattice()
```

K3曲面に関連するBeauville-Bogomolov-Fujiki形式に対応する整数格子を返します。

# 例

```jldoctest
julia> L = k3_lattice();

julia> is_unimodular(L)
true

julia> signature_tuple(L)
(3, 0, 19)
```
