```
create_surface_filter(cache::BasicILMCache)
```

サーフェスフィルタリング行列演算子 $\tilde{R}^T R$ を作成します。ここで、$\tilde{R}^T$ は補間演算子の修正バージョンを表します。得られた行列は、サーフェスデータに適用して高周波成分をフィルタリングすることができます。
