```
HPolygonOpt{N, VN<:AbstractVector{N}} <: AbstractHPolygon{N}
```

制約表現における凸多角形を表す型で、そのエッジは法線方向に対して反時計回りにソートされています。この実装は、[`HPolygon`](@ref) の洗練されたバージョンです。

### フィールド

  * `constraints` – 法線方向に反時計回りにソートされた線形制約のリスト
  * `ind`         – サポートベクトル/関数を評価するための検索を開始する制約リスト内のインデックス

### 注意事項

さらなるコンストラクタ引数：

  * `sort_constraints`  – （オプション、デフォルト: `true`）制約をソートするためのフラグ（ソートされていることはこの型の前提条件です）
  * `check_boundedness` – （オプション、デフォルト: `false`）制約が多角形を有界にするかどうかをチェックするためのフラグ（有界性はこの型の前提条件です）
  * `prune`             – （オプション、デフォルト: `true`）冗長な制約を削除するためのフラグ

この構造体は、互いに近い方向の大きなシーケンスでサポートベクトル/関数を評価するために最適化されています。戦略は、サポートベクトル計算における最適値の検索をウォームスタートするために使用できるインデックスを持つことです。

オプション `sort_constraints` は、反時計回りに制約を自動的にソートする機能を無効にするために使用できます。これはこの型の不変条件です。あるいは、空の制約リストで `HPolygonOpt` を構築し、その後 `addconstraint!` を使用して反復的に埋めることもできます。

同様に、オプション `prune` は冗長な制約の自動的なプルーニングを無効にするために使用できます。

もう一つの型の前提は、多角形が有界であることです。オプション `check_boundedness` を使用してこれを確認できます。このオプションはデフォルトで無効になっているため、制約の反復的な追加を明示的に許可したい場合、最初に空の制約リスト（無限大の集合を表す）を構築する必要があります。ユーザーは、制約が実際に有界な集合を記述する前に `HPolygonOpt` が使用されないようにする必要があります。
