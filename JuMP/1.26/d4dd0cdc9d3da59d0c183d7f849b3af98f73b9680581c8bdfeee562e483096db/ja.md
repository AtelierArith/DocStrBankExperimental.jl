```
relax_integrality(model::GenericModel)
```

`model`を修正して、すべてのバイナリおよび整数制約を「緩和」します。具体的には、

  * バイナリ制約は削除され、変数が区間 $[0, 1]$ に制約されるように必要に応じて変数の境界が厳しくなります。
  * 整数制約は変数の境界を変更することなく削除されます。
  * 半連続または半整数制約が存在する場合はエラーが発生します（将来的にこれらのサポートが追加される可能性があります）。
  * その他のすべての制約は無視されます（そのまま残ります）。これには、SOSやインジケーター制約のような離散制約が含まれます。

元のモデルを復元するために引数なしで呼び出すことができる関数を返します。この関数の動作は、その間に影響を受ける変数に追加の変更が加えられた場合は未定義です。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x, Bin);

julia> @variable(model, 1 <= y <= 10, Int);

julia> @objective(model, Min, x + y);

julia> undo_relax = relax_integrality(model);

julia> print(model)
Min x + y
Subject to
 x ≥ 0
 y ≥ 1
 x ≤ 1
 y ≤ 10

julia> undo_relax()

julia> print(model)
Min x + y
Subject to
 y ≥ 1
 y ≤ 10
 y integer
 x binary
```
