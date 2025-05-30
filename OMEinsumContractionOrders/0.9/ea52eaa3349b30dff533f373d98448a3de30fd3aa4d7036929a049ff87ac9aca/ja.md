```
SABipartite{RT,BT}
SABipartite(; sc_target=25, ntrials=50, βs=0.1:0.2:15.0, niters=1000
    max_group_size=40, greedy_config=GreedyMethod(), initializer=:random)
```

最適化されたeinsumコードの収束順序をシミュレーテッドアニーリングの二部分割 + 貪欲アプローチを使用して行います。このプログラムは、最初にシミュレーテッドアニーリングを使用してテンソルをいくつかのグループに再帰的に分割し、`max_group_size`で指定された最大グループサイズと`sc_target`で指定された最大空間複雑性を持ちます。その後、各グループ内の収束順序を貪欲探索アルゴリズムで見つけます。他の引数は次のとおりです。

  * `size_dict`は脚の次元を指定する辞書です。
  * `sc_target`はターゲット空間複雑性で、`log2(最大テンソルの要素数)`として定義されます。
  * `max_group_size`は貪欲探索に使用できる最大サイズです。
  * `βs`は逆温度`1/T`のリストです。
  * `niters`は各温度での反復回数です。
  * `ntrials`は異なるランダムシードでの繰り返し回数です。
  * `sub_optimizer`は二部グラフの最適化手法で、`GreedyMethod()`または`TreeSA()`を選択できます。
  * `initializer`はパーティション構成の初期化子で、`:random`または`：greedy`（遅いがより良い）を選択できます。

### 参考文献

  * [ハイパー最適化されたテンソルネットワーク収束](https://arxiv.org/abs/2002.01935)

```
