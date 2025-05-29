```
direct_sum(G::FinGenAbGroup...) -> FinGenAbGroup, Vector{FinGenAbGroupHom}
```

有限個のアーベル群 $G_i$ の直和 $D$ を返し、同時に射影 $G_i \to D$ を返します。

有限アーベル群の場合、有限直和と有限直積は一致し、それゆえ双積と呼ばれます。$D$ を直積として得たい場合は、射影 $D \to G_i$ とともに `direct_product(G...)` を呼び出すべきです。$D$ を双積として得たい場合は、射影と射影を伴って `biproduct(G...)` を呼び出すべきです。

そうでなければ、後で `canonical_injections(D)` または `canonical_projections(D)` を呼び出すこともできます。
