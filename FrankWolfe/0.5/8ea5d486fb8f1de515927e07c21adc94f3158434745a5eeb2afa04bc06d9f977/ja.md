```
blended_conditional_gradient(f, grad!, lmo, x0)
```

ブレンド条件付き勾配アルゴリズムのエントリーポイント。Braun, Gábor, et al. "Blended conditonal gradients" ICML 2019を参照してください。この手法は、[`FrankWolfe.away_frank_wolfe`](@ref)のようなアクティブセットで動作し、アクティブな頂点の凸包上で勾配降下を行い、重みが0に下がった頂点を削除し、遅延的に線形オラクルを呼び出すことで新しい頂点を追加します。
