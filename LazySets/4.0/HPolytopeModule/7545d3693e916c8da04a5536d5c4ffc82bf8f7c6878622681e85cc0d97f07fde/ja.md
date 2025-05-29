```
vertices_list(P::HPolytope; [backend]=nothing, [prune]::Bool=true)
```

制約表現における多面体の頂点のリストを返します。

### 入力

  * `P`       – 制約表現における多面体
  * `backend` – （オプション、デフォルト: `nothing`）多面体計算のためのバックエンド
  * `prune`   – （オプション、デフォルト: `true`）冗長な頂点を削除するフラグ

### 出力

頂点のリスト。

### アルゴリズム

多面体が1次元（または2次元）の場合、区間（または制約表現における多角形）に変換され、それぞれの最適化された `vertices_list` 実装が使用されます。

1次元および2次元の場合は、`backend` を渡すことで `Polyhedra` バックエンドを使用することも可能です。

多面体が2次元でない場合、具体的な多面体操作ライブラリ `Polyhedra` が使用されます。実際の計算は指定されたバックエンドによって行われます。`LazySets` で使用されるデフォルトのバックエンドについては `default_polyhedra_backend(P)` を参照してください。サポートされているバックエンドに関する詳細は [Polyhedraのドキュメント](https://juliapolyhedra.github.io/Polyhedra.jl/) を参照してください。
