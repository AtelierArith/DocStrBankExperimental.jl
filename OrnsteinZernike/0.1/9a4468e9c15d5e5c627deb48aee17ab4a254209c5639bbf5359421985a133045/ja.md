```
Exact <: Method
```

システムを正確に解決します。これは特定のシステムにのみ実装されています。

現在、実装されている正確なメソッドは

  * パーカス・イェビック閉包を持つ三次元単一成分ハードスフィア系 [1]
  * パーカス・イェビック閉包を持つ三次元多成分加法的ハードスフィア系 [2]
  * パーカス・イェビック閉包を持つ一次元単一成分ハードスフィア系 [3]
  * パーカス・イェビック閉包を持つ五次元単一成分ハードスフィア系 [3]

次のように構築します。

`Exact(;  M=1000, dr = 10.0/M)`

ここで、`M`は正確な解が評価される点の数であり、`dr`はグリッド間隔です。これらはフーリエ変換を行うために使用されます。

例

`method = Exact()`

`method = Exact(M=1000)`

`method = Exact(M=1000, dr=0.01)`

参考文献:

1. Wertheim, M. S. "Exact solution of the Percus-Yevick integral equation for hard spheres." Physical Review Letters 10.8 (1963): 321.
2. Baxter, R. J. "Ornstein–Zernike relation and Percus–Yevick approximation for fluid mixtures." The Journal of Chemical Physics 52.9 (1970): 4559-4562.
3. Leutheusser, E. "Exact solution of the Percus-Yevick equation for a hard-core fluid in odd dimensions." Physica A: Statistical Mechanics and its Applications 127.3 (1984): 667-676.
