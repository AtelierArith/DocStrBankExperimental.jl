```
lspin(p::Union{Particle, PDGID, Integer})
```

Lを2S+1として返します。

これはメソンにのみ有効です。それ以外の場合は`nothing`が返されます。PDGIDが9XXXXXX（N=9）のメソンは実験的に良く知られている粒子ではなく、`nothing`が返されます。
