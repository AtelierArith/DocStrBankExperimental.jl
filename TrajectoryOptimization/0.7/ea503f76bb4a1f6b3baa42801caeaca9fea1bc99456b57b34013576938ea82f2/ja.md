```
ConstraintList
```

軌道最適化問題に含まれる制約のセットを格納します。制約のタイプ [`AbstractConstraint`](@ref) のリストと、制約が適用されるノットポイントのリストが含まれています。各制約は、連続したノットポイントのセットに適用されるものと仮定されています。

`ConstraintList` は、`AbstractConstraint` に対する反復処理とインデックス付けをサポートし、`zip(cons::ConstraintList)` を介して制約とそれが適用されるノットポイントのインデックスの両方を反復処理します。

制約は [`add_constraint!`](@ref) メソッドを介して追加され、制約の次元が適用されるノットポイントでの状態および制御次元と一致していることが確認されます。

各ノットポイントでの制約の総数は、[`num_constraints`](@ref) メソッドを使用して照会できます。

# コンストラクタ

```
ConstraintList(nx, nu)
ConstraintList(n, m, N)
ConstraintList(models)
```

ここで `nx` と `nu` は、各ノットポイントでの状態および制御次元を指定する `N` 次元ベクトルです。これらが全体の軌道で同じである場合、ユーザーは2番目のコンストラクタを使用できます。あるいは、`DiscreteDynamics` モデルのベクトルである `models` から自動的に構築することもできます。
