```
ideal(O::RelNumFieldOrder{T, S}, x::RelSimpleNumFieldElem{T}, y::RelSimpleNumFieldElem{T}, a::S, b::S; check::Bool = true) -> RelNumFieldOrderIdeal{T, S}
```

理想 $x\cdot a + y\cdot b$ を $\mathcal O$ のために作成します。`check` が設定されている場合、これらの要素が理想を定義するかどうかがチェックされます。
