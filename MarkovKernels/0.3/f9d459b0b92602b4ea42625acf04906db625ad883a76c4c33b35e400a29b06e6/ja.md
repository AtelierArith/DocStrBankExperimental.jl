```
htransform(K::AbstractMarkov, L::AbstractLikelihood)
```

マルコフカーネル Kout と尤度 Lout を計算します。次のようになります。

Lout(z) = ∫ L(x) K(x, z) dx, および Kout(x, z) = L(x) K(x, z) / Lout(z)
