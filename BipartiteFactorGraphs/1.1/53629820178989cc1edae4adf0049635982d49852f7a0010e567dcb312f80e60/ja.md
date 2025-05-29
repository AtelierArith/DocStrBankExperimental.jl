```
density(g::BipartiteFactorGraph)
```

グラフの密度を返します。

二部グラフの場合、密度は実際のエッジの数と変数ノードと因子ノード間の最大可能エッジ数（これは num*variables(g) * num*factors(g) です）との比率として定義されます。
