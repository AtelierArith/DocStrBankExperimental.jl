```
force_layout(p::Poset)
```

カバー有向グラフのエッジがスプリングのように作用し、ノードが反発する粒子のように作用する順序集合を計算します。y座標は `layered_layout_2` によって決定され、その後x座標を最適化します。時々良い画像を生成しますが、動作が遅くなることがあります。
