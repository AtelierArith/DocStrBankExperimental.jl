```
biproduct(G::FinGenAbGroup...) -> FinGenAbGroup, Vector{FinGenAbGroupHom}, Vector{FinGenAbGroupHom}
```

有限個のアーベル群 $G_i$ の直積 $D$ を返し、$D \to G_i$ の射影と $G_i \to D$ の注入も返します。

有限アーベル群の場合、有限直和と有限直積は一致し、したがってそれらは双積と呼ばれます。$D$ を直和として得たい場合は、注入 $G_i \to D$ とともに `direct_sum(G...)` を呼び出すべきです。$D$ を直積として得たい場合は、射影 $D \to G_i$ とともに `direct_product(G...)` を呼び出すべきです。

そうでなければ、後で `canonical_injections(D)` または `canonical_projections(D)` を呼び出すこともできます。
