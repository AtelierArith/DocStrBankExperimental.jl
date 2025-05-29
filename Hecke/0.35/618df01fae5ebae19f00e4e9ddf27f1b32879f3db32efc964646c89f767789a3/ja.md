```
biproduct(G::FinGenAbGroup...) -> FinGenAbGroup, Vector{FinGenAbGroupHom}, Vector{FinGenAbGroupHom}
```

有限個のアーベル群 $G_i$ の直積 $D$ を返し、さらに射影 $D \to G_i$ と埋め込み $G_i \to D$ を返します。

有限アーベル群の場合、有限直和と有限直積は一致し、したがってそれらはバイプロダクトと呼ばれます。もし $D$ を直和として得たい場合は、埋め込み $G_i \to D$ とともに `direct_sum(G...)` を呼び出すべきです。もし $D$ を直積として得たい場合は、射影 $D \to G_i$ とともに `direct_product(G...)` を呼び出すべきです。

そうでなければ、後で `canonical_injections(D)` または `canonical_projections(D)` を呼び出すこともできます。
