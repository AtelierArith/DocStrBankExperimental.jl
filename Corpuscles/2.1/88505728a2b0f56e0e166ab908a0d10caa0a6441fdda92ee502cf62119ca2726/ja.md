```
S(p::Union{Particle, PDGID, Integer})
```

スピン S を返します。

これはメソンにのみ有効です。それ以外の場合は `nothing` が返されます。PDGID が 9XXXXXX (N=9) のメソンは実験的に良く知られている粒子ではなく、`nothing` が返されます。
