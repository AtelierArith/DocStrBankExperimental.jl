```
shell_cluster_partitioning(fens, fes, nelperpart = 50, crease_ang = 30/180*pi, cluster_max_normal_deviation = 2 * crease_ang)
```

シェル構造の粗いグリッド（クラスタ）分割を計算します。

要素は、分割ごとの要素数（`nelperpart`）に基づいて `ShellStructureTopo.create_partitions()` を使用してサブセットに分割されます。次に、要素サブセットのノードがクラスタに割り当てられます。
