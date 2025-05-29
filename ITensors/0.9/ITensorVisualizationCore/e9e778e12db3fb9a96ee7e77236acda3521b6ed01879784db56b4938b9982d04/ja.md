```
@visualize
```

ITensorsの収縮を視覚化し、収縮の結果を返します。

収縮は、`*`で収縮された一連のITensorsの形で記述されるべきです。

# 例

```julia
using ITensors
using ITensorUnicodePlots # バックエンドをロードしないとプロットは作成されません

i = Index(2, "index_i")
j = Index(10, "index_j")
k = Index(40, "index_k")
l = Index(40, "index_l")
m = Index(40, "index_m")
A = random_itensor(i, j, k)
B = random_itensor(i, j, l, m)
C = random_itensor(k, l)

# 共通のインデックスでテンソルを収縮し
# 結果を視覚化します
ABC = @visualize A * B * C

AB = @visualize A * B
# プロットの間に一時停止するにはreadline()を使用します
readline()
ABC = @visualize AB * C vertex_labels = ["A*B", "C"]
readline()

# 後で見るために結果を図に保存します
AB = @visualize fig1 A * B
ABC = @visualize fig2 AB * C vertex_labels = ["A*B", "C"]

display(fig1)
readline()
display(fig2)
readline()
```

# キーワード引数:

  * `vertex_labels`: ダイアグラムの頂点に表示するカスタムテンソルラベル。指定しない場合は、マクロへの入力から自動的に決定されます。
  * `edge_labels=IndexLabels()`: エッジラベルのリストまたは、どのように作成されるべきかを指定する`AbstractEdgeLabels`オブジェクト。
  * `arrow_show`: エッジに矢印を表示するかどうか。
