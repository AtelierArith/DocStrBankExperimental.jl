```
restrict_scalars(V::AbstractSpace, K::QQField,
                                   alpha::FieldElem = one(base_ring(V)))
                                                -> QuadSpace, AbstractSpaceRes
```

空間 $(V, \Phi)$ と基底代数 `E` の部分体 `K` が与えられたとき、スカラーを `K` に制限することによって得られる二次空間 `W` と、スカラーを元に戻すための写像 `f` を返します。制限された形式は $Tr \circ \Phi$ によって与えられ、ここで $Tr: E \to K$ はトレース形式です。再スケーリング因子 $\alpha$ はデフォルトで 1 に設定されています。

現時点では、スカラーを $\mathbb Q$ に制限することしかできないことに注意してください。
