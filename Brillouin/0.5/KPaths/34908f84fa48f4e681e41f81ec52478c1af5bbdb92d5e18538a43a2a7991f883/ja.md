```
latticize(kpi::KPathInterpolant{D}, basis::AbstractVector{<:AbstractVector{<:Real}})
```

補間された**k**-パス `kpi` を直交基底から格子基底に変換します。ここで、(原始的な) 逆格子ベクトルは `basis` です。

もし `kpi` が直交基底にない場合（すなわち、`setting(kpi) == LATTICE` の場合）、`kpi` はそのまま返されます。
