DenseNautyGraph(size::Int)   DenseNautyGraph(adj::Matrix)   DenseNautyGraph(g::AbstractGraph)

新しい密なNautyグラフを構築します。

密なNautyグラフはビット行列です：グラフに`n`の頂点がある場合、それは`(WORDSIZE*m)×n`のビット行列としてコーディングされます。ここで、`m=(n+WORDSIZE-1)÷WORDSIZE`です。その行列の各列は、サイズ`m`のメモリのチャンクを表し、`i`番目の列は`i`番目の頂点の隣接リストを表します。ビットは各ワード内で逆順になっているため、`i`番目の頂点が`j`番目の頂点に接続されているかどうかを知るには、フィールド`data[setpos(j),i]`を確認してください。
