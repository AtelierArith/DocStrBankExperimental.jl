## ダイクストラ

```
ダイクストラのアルゴリズムを使用して最短経路を計算します。
d = dijkstra(A,u) は、ダイクストラのアルゴリズムを使用して、頂点 u から到達可能なすべてのノードへの最短経路を計算します。
グラフは、重み付きスパース行列 A によって与えられ、A(i,j) は頂点 i と j の間の距離です。出力ベクトル d では、エントリ d[v] は頂点 u と頂点 v の間の最小距離です。
u から到達不可能な頂点 w は d(w)=Inf です。
pred は実際の最短経路を生成するための前駆体ツリーです。
前駆体ツリーでは、pred[v] は最短経路における v の前の頂点であり、pred[u]=0 です。到達不可能な頂点は pred[w]=0 でもあります。
ネットワークが無重みの場合は、代わりに bfs を使用してください。
```

## 関数

  * (d,pred) = dijkstra(A::MatrixNetwork,u::Int64)
  * (d,pred) = dijkstra{F}(A::SparseMatrixCSC{F,Int64},u::Int64)

## 例

```
# ロサンゼルス (LAX) と
# ミネソタ州ロチェスター (RST) の間の最小旅行時間を見つけます。

(A,xy,labels) = load_matrix_network_metadata("airports")
A = -A; # 空港データの奇妙なエンコーディングを修正
lax = 247; rst = 355
(d,pred) = dijkstra(A,lax)
@printf("最小時間: %d",d[rst]); # パスを表示
@printf("パス:")
u = rst
while(u != lax)
    @printf("%s <-- ", labels[u])
    u = pred[u];
    if (u == lax)
        @printf("%s", labels[lax])
    end
end
```
