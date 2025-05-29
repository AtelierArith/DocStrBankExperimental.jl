```
direct_product(G::FinGenAbGroup...) -> FinGenAbGroup, Vector{FinGenAbGroupHom}
```

有限個のアーベル群 $G_i$ の直積 $D$ を返し、プロジェクション $D \to G_i$ も返します。

有限アーベル群の場合、有限直和と有限直積は一致し、したがって双積と呼ばれます。$D$ を直和として得たい場合は、$D \to G_i$ の注入も含めて `direct_sum(G...)` を呼び出すべきです。$D$ を双積として得たい場合は、プロジェクションと注入の両方を含めて `biproduct(G...)` を呼び出すべきです。

そうでなければ、後で `canonical_injections(D)` または `canonical_projections(D)` を呼び出すこともできます。
