```
edit_distance(G₁::AbstractGraph, G₂::AbstractGraph)
```

グラフ `G₁` と `G₂` の間の編集距離を計算します。グラフ `G₁` をグラフ `G₂` に変換するための最小編集コストと編集パスを返します。編集パスは、頂点操作を表す頂点のペアのシーケンス $(u,v) ∈ [0,|G₁|] × [0,|G₂|]$ で構成されます：

  * $$
    (0,v)
    $$

    : 頂点 $v ∈ G₂$ の挿入
  * $$
    (u,0)
    $$

    : 頂点 $u ∈ G₁$ の削除
  * $$
    (u>0,v>0)
    $$

    : 頂点 $u ∈ G₁$ を頂点 $v ∈ G₂$ に置き換え

### オプション引数

  * `insert_cost::Function=v->1.0`
  * `delete_cost::Function=u->1.0`
  * `subst_cost::Function=(u,v)->0.5`

デフォルトでは、アルゴリズムは定数操作コストを使用します。ユーザーは、頂点ラベル μ₁ (G₁ 用) と μ₂ (G₂ 用) から計算された古典的なミンコフスキーコストを提供して、検索をさらにガイドすることができます。例えば：

```
edit_distance(G₁, G₂, subst_cost=MinkowskiCost(μ₁, μ₂))
```

  * `heuristic::Function=DefaultEditHeuristic`: デフォルトのヒューリスティックが満足できない場合に A* 検索に提供されるカスタムヒューリスティック。

### パフォーマンス

  * 2つのグラフ $|G₁| < |G₂|$ の場合、`edit_distance(G₁, G₂)` は `edit_distance(G₂, G₁)` よりも計算が速いです。関与するコストが同等であれば、引数を入れ替えることを検討してください。
  * 単純なミンコフスキーコストの使用は、パフォーマンスを大幅に改善する可能性があります。
  * 操作コストを設計する際に頂点属性を活用してください。

### 参考文献

  * RIESEN, K., 2015. 構造的パターン認識とグラフ編集距離: 近似アルゴリズムと応用. (第2章)

### 著者

  * Júlio Hoffimann Mendes (juliohm@stanford.edu)

# 例

```jldoctest
julia> g1 = SimpleDiGraph([0 1 0 0 0; 0 0 1 0 0; 1 0 0 1 0; 0 0 0 0 1; 0 0 0 1 0]);

julia> g2 = SimpleDiGraph([0 1 0; 0 0 1; 1 0 0]);

julia> edit_distance(g1, g2)
(3.5, Tuple[(1, 2), (2, 1), (3, 0), (4, 3), (5, 0)])
```
