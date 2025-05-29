```
vertextocellmap(mesh) -> vertextocells, numneighbors
```

Vの数とMの最大数を持つV×M配列`vertextocells`を計算します。ここで、Vは頂点の数、Mは任意の頂点に隣接するセルの最大数です。`vertextocells[v,i]`は、`v`-th頂点に隣接する`i`番目のセルの`mesh`内のインデックスです。`numneighbors[v]`には、`v`-th頂点に隣接するセルの数が含まれます。

このメソッドは、メッシュの接続行列を効率的に計算することを可能にします。
