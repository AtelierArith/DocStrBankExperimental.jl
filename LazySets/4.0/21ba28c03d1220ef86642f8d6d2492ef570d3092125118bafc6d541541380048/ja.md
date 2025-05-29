```
vertices_list(P::AbstractHPolygon;
              apply_convex_hull::Bool=true,
              check_feasibility::Bool=true)
```

制約表現における多角形の頂点のリストを返します。

### 入力

  * `P`                 – 制約表現の多角形
  * `apply_convex_hull` – （オプション、デフォルト: `true`）制約の交差を凸包で後処理するためのフラグ
  * `check_feasibility` – （オプション、デフォルト: `true`）多角形が空であるかどうかを確認するためのフラグ（空の多角形の場合の正確性に必要）

### 出力

頂点のリスト。

### 注意事項

構造上、`AbstractHPolygon` は冗長な頂点を含むべきではありません。それでも、`apply_convex_hull` 引数はデフォルトで有効になっており、潜在的な重複頂点を削除します。これらは数値的不安定性により存在する可能性があります。

```jldoctest
julia> p = HPolygon([HalfSpace([1.0, 0.0], 1.0),
                     HalfSpace([0.0, 1.0], 1.0),
                     HalfSpace([-1.0, 0.0], -1.0),
                     HalfSpace([0.0, -1.0], -1.0)]);

julia> vertices_list(p, apply_convex_hull=false)
4-element Vector{Vector{Float64}}:
 [1.0, 1.0]
 [1.0, 1.0]
 [1.0, 1.0]
 [1.0, 1.0]
```

各制約が次の頂点までの「適切な」距離を持つことが知られている場合、このステップはスキップできます。

### アルゴリズム

各頂点を半空間によって定義された連続する線の交点として計算します。`check_feasibility` が有効な場合、次に多角形の制約が実際に実現可能であったか（すなわち、*正しい*方向を指していたか）を確認します。これには、すべての頂点の*平均*を計算し、各制約へのメンバーシップを確認します。 ```
