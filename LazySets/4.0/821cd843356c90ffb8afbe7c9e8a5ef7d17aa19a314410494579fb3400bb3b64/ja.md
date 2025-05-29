# 拡張ヘルプ

```
isempty(P::LazySet, witness::Bool=false;
        [use_polyhedra_interface]::Bool=false, [solver]=nothing,
        [backend]=nothing)
```

### 入力

  * `witness` – （オプション、デフォルト: `false`）有効化された場合、ウィットネスを計算する
  * `use_polyhedra_interface` – （オプション、デフォルト: `false`）`true`の場合、空集合テストに`Polyhedra`インターフェースを使用する
  * `solver`  – （オプション、デフォルト: `nothing`）LPソルバーのバックエンド；提供されていない場合は`default_lp_solver`を使用
  * `backend` – （オプション、デフォルト: `nothing`）`Polyhedra`における多面体計算のバックエンド；提供されていない場合は`default_polyhedra_backend(P)`を使用

### 注意事項

この実装は`P`が多面体であることを前提としています。

`backend`のデフォルト値は内部で設定され、`use_polyhedra_interface`オプションが設定されているかどうかに依存します。オプションが設定されている場合、`default_polyhedra_backend(P)`を使用します。

`use_polyhedra_interface`が`true`の場合、ウィットネスの生成はサポートされていません。

### アルゴリズム

アルゴリズムは`P`の制約に対する実現可能性LPを設定します。`use_polyhedra_interface`が`true`の場合、`Polyhedra.isempty`を呼び出します。それ以外の場合、内部でLPを設定します。
