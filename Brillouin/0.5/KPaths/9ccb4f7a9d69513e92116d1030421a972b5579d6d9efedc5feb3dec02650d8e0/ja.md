```
latticize(kp::KPath{D}, basis::AbstractVector{<:AbstractVector{<:Real}})
```

**k**-パス `kp` を直交基底から格子基底に変換し、(原始的な) 逆格子ベクトル `basis` を使用します。

もし `kp` が直交基底にない場合 (すなわち、`setting(kp) == LATTICE` の場合)、`kp` はそのまま返されます。
