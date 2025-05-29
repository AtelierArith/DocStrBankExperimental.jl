```
latticize(c::Cell{D}, basis::AbstractVector{<:AbstractVector{<:Real}})
```

ウィグナー-ザイツセル `c` を直交基底から格子基底に変換し、(原始)逆格子ベクトル `basis` を使用します。

`c` が直交基底にない場合 (すなわち、`setting(c) == LATTICE` の場合)、`c` はそのまま返されます。
