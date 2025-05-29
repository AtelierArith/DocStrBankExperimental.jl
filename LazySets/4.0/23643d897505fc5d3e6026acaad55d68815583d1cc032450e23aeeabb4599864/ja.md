```
intersection(P1::AbstractPolyhedron{N}, P2::AbstractPolyhedron{N};
             [backend]=default_lp_solver(N), [prune]::Bool=true) where {N}
```

二つの多面体の交差を計算します。

### 入力

  * `P1`      – 多面体
  * `P2`      – 多面体
  * `backend` – （オプション、デフォルト: `default_lp_solver(N)`）冗長な制約を削除するために使用されるLPソルバー; 詳細は*ノート*セクションを参照してください
  * `prune`   – （オプション、デフォルト: `true`）冗長な制約を削除するためのフラグ

### 出力

`P1`と`P2`の交差から得られる`HPolyhedron`、冗長な制約が削除されたもの、または交差が空である場合は空集合。引数の一つが多面体である場合、結果は`HPolytope`になります。

### ノート

ソルバーバックエンドのデフォルト値は`default_lp_solver(N)`であり、交差の冗長な制約を削除するために実行される実行可能性LPを実行するために使用されます。

`Polyhedra`ライブラリを使用したい場合は、適切なバックエンドを渡してください。例えば、デフォルトのPolyhedraライブラリには`default_polyhedra_backend(P)`を使用するか、CDDライブラリには`CDDLib.Library()`を使用します。

デフォルトのPolyhedraライブラリを使用した制約の削除にはいくつかの欠点があります; 例えば、#1038やPolyhedra#146を参照してください。その場合、この関数を呼び出す前に交差の空性を確認する方が安全です。

### アルゴリズム

この実装は、`constraints_list`メソッドから得られた二つの集合の制約を統合します。
