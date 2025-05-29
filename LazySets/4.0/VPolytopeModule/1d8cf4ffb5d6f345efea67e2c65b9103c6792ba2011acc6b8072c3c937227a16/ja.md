```
remove_redundant_vertices(P::VPolytope; [backend]=nothing, [solver]=nothing)
```

与えられた多面体の冗長な頂点を削除することによって得られる多面体を返します（頂点表現）。

### 入力

  * `P`       – 頂点表現の多面体
  * `backend` – （オプション、デフォルト: `nothing`）多面体計算のためのバックエンド；詳細については `default_polyhedra_backend(P)` または              [Polyhedraのドキュメント](https://juliapolyhedra.github.io/)              を参照してください
  * `solver`  – （オプション、デフォルト: `nothing`）必要に応じてバックエンドで使用される線形計画ソルバー；詳細については              `default_lp_solver_polyhedra(N)` を参照してください

### 出力

与えられた多面体の凸包がその頂点である新しい多面体。

### 注意事項

冗長な頂点を削除することに関連する最適化問題は `Polyhedra` によって処理されます。多面体計算バックエンドがLPソルバーを必要とする場合、しかしそれが指定されていない場合は、`default_lp_solver_polyhedra(N)` を使用してそのソルバーを定義します。そうでなければ、多面体バックエンドの冗長性削除関数が使用されます。
