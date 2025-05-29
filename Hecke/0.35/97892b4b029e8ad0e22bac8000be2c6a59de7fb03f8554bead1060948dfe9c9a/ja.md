```
restrict_scalars(L::AbstractLat, K::QQField,
                                 alpha::FieldElem = one(base_field(L))) -> ZZLat
```

与えられた格子 `L` が空間 $(V, \Phi)$ にあるとき、数体 `K` に対して $(V, \alpha\Phi)$ のスカラーを制限することによって得られる $\mathcal O_K$-格子を返します。リスケーリング係数 $\alpha$ はデフォルトで 1 に設定されています。

現時点では、スカラーを制限できるのは $\mathbb Q$ のみであることに注意してください。
