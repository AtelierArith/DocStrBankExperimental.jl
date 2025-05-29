```
restrict_scalars(L::AbstractLat, f::AbstractSpaceRes) -> ZZLat
```

与えられた格子 `L` が空間 $(V, \Phi)$ にあり、`f` が $(V, \alpha\Phi)$ のスカラーを数体 `K` に制限するための写像であるとき、ここで $\alpha$ は `L` の基底代数にある。`L` から `f` に関して得られる関連する $\mathcal O_K$-格子を返します。

現時点では、スカラーを $\mathbb Q$ にのみ制限できることに注意してください。
