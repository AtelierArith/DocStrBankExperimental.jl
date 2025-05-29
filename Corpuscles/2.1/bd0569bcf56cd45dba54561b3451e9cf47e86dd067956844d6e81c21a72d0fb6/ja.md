```
L(p::Union{Particle, PDGID, Integer})
```

軌道角運動量 L を返します。

これはメソンにのみ有効です。それ以外の場合は `nothing` が返されます。PDGID が 9XXXXXX (N=9) の種類のメソンは実験的に良く知られていない粒子であり、`nothing` が返されます。
