```
WithGraph(model, g::GNNGraph; traingraph=false)
```

`model`をラップし、グラフ`g`に結びつける型です。フォワードパスでは、特徴配列のみを入力として受け取り、`model(g, x...; kws...)`を返します。

`traingraph=false`の場合、グラフのパラメータは勾配更新における`trainable`パラメータの一部にはなりません。

# 例

```julia
g = GNNGraph([1,2,3], [2,3,1])
x = rand(Float32, 2, 3)
model = SAGEConv(2 => 3)
wg = WithGraph(model, g)
# `wg`にグラフを渡す必要はありません
@assert wg(x) == model(g, x)

g2 = GNNGraph([1,1,2,3], [2,4,1,1])
x2 = rand(Float32, 2, 4)
# WithGraphは新しいグラフが与えられた場合、内部のグラフを無視します。
@assert wg(g2, x2) == model(g2, x2)
```
