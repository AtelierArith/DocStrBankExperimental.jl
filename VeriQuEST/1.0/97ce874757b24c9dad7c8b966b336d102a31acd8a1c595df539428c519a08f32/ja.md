```
entangle_graph!(::Client, mg)
```

この関数は、MBQCモデルにおけるクライアントのメタグラフの量子状態をエンタングルします。最初にメタグラフから量子状態を取得し、メタグラフからグラフを作成します。次に、グラフ内の各エッジに対して、ソースおよび宛先の頂点に制御位相反転操作を適用します。

# 引数

  * `::Client`: クライアントオブジェクト。
  * `mg`: プロパティが追加されるメタグラフ。

# 例

```julia
client = Client()
mg = MetaGraphs.MetaGraph(graph)
entangle_graph!(client, mg)
```
