```
ideal(O::RelNumFieldOrder{T, S}, a::S; check::Bool = true) -> RelNumFieldOrderIdeal{T, S}
```

理想 $a \cdot \mathcal O$ を $\mathcal O$ のために作成します。`check` が設定されている場合、$a$ が（整数）理想を定義するかどうかがチェックされます。
