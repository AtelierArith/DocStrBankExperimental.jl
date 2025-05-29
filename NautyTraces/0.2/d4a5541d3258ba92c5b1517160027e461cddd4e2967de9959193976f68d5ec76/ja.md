DenseNautyDiGraph(size::Int)   DenseNautyDiGraph(adj::Matrix)   DenseNautyDiGraph(g::AbstractGraph)

新しい密なNauty有向グラフを構築します。

密なNauty有向グラフはビット行列です：グラフに`n`頂点がある場合、それは`(WORDSIZE*m)×n`ビット行列としてコーディングされ、`m=(n+WORDSIZE-1)÷WORDSIZE`となります。その行列の各列はサイズ`m`のメモリのチャンクを表し、`i`番目の列は`i`番目の頂点の隣接リストを表します。ビットは各ワード内で逆順になっているため、`i`番目の頂点が`j`番目の頂点に接続されているかどうかを知るには、フィールド`data[setpos(j),i]`を確認してください。
