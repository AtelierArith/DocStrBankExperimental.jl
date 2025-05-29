```
vertices_list(P::AbstractPolyhedron; check_boundedness::Bool=true)
```

制約表現における多面体の頂点のリストを返します。

### 入力

  * `P`                 – 制約表現の多面体
  * `check_boundedness` – （オプション、デフォルト: `true`）`true` の場合、多面体が有界かどうかをチェックします

### 出力

`P` の頂点のリスト、または `P` が無限大の場合はエラー。

### 注意事項

この関数は、多面体が無限大の場合にエラーをスローします。それ以外の場合、多面体は `HPolytope` に変換され、その頂点のリストが計算されます。

### 例

```jldoctest
julia> P = HPolyhedron([HalfSpace([1.0, 0.0], 1.0),
                        HalfSpace([0.0, 1.0], 1.0),
                        HalfSpace([-1.0, 0.0], 1.0),
                        HalfSpace([0.0, -1.0], 1.0)]);

julia> length(vertices_list(P))
4
```
