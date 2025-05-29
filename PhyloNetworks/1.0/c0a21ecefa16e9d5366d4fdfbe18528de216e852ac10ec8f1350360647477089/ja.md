```
biconnectedcomponents(network, ignoreTrivial=false)
```

Tarjanのアルゴリズムを使用して双連結成分（別名「ブロブ」）を計算します。

出力：エッジの配列の配列。

  * 配列の長さはブロブの数です
  * 各要素は、特定のブロブ内のすべてのエッジの配列です。

これらのブロブは後順で返されますが、ブロブ内のエッジは必ずしもトポロジカル順にソートされているわけではありません。`ignoreTrivial`がtrueの場合、単一のエッジからなる自明な成分は返されません。ネットワークは接続されていると仮定されます。

*警告*: ノードについては、フィールド`intn2`と`intn1`がアルゴリズム中に変更されます。これらは、ノードの「インデックス」（訪問時刻）、「ローポイント」、およびノードの「親」を格納するために使用されます。エッジについては、フィールド`boole2`が変更され、エッジがすでに訪問されたかどうかを格納します。

参考文献：

  * [Tarjan (1972)](http://epubs.siam.org/doi/pdf/10.1137/0201010)のp. 153。深さ優先探索と線形グラフアルゴリズム、SIAM Journal on Computing, 1(2):146-160
  * [geeksforgeeks](https://www.geeksforgeeks.org/biconnected-components/)には、エラーがあります（2018-01-30現在）：`elif v != parent[u] and low[u] > disc[v]:`（pythonバージョン）は`elif v != parent[u] and disc[u] > disc[v]:`に置き換える必要があります。
  * この[url](https://www.cs.cmu.edu/~avrim/451f12/lectures/biconnected.pdf)に良い説明があります。
