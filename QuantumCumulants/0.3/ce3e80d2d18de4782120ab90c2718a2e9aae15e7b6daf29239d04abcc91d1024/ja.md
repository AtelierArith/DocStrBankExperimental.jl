```
Pauli <: QSym
```

二レベルスピン系のパウリ演算子 σx、σy、σz を表す [`PauliSpace`](@ref) 上のパウリ演算子。フィールド軸は x、y、z をそれぞれ 1、2、3 として表します。使用される書き換えルールは σj⋅σk → δjk + i⋅ϵjkl⋅σl です。

# 例

```
julia> h = PauliSpace("Spin-1/2")
ℋ(Spin-1/2)

julia> σx = Pauli(h,:σ,1)
σx
```
