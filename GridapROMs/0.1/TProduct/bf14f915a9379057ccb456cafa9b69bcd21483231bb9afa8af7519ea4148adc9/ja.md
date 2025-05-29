```
struct TProductFESpace{S} <: SingleFieldFESpace
  space::S
  spaces_1d::Vector{<:SingleFieldFESpace}
  trian::TProductTriangulation
end
```

テンソル積単一フィールド `FESpace` は、長さ D の 1-D `FESpace` のベクトル `spaces_1d` を格納し、D 次元の `FESpace` `space` はそれらのテンソル積として定義されます。テンソル積三角形分割 `trian` は、`MultiField` シナリオに渡す際の互換性の問題を避けるためにフィールドとして提供されます。
