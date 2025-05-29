```
kpm_eval(x::T, kpm_expansion::KPMExpansion{T}) where {T<:AbstractFloat}
```

実数値 $x$ を評価します。ここで $x$ は `bounds[1] < x < bound[2]` の範囲にあり、関数 $F(\bullet)$ はベクトル `coefs` によって与えられるコーエフィシエントを持つチェビシェフ展開で表されます。
