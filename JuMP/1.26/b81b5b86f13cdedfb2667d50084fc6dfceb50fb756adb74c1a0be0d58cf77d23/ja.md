```
fix_discrete_variables([var_value::Function = value,] model::GenericModel)
```

`model`を修正して、すべてのバイナリおよび整数変数を`var_value(x)`の固定範囲を持つ連続変数に変換します。

## 返り値

引数なしで呼び出すことができる関数を返し、元のモデルを復元します。この関数の動作は、影響を受ける変数に対して追加の変更が行われた場合には未定義です。

## 注意事項

  * 半連続または半整数制約が存在する場合、エラーが発生します（将来的にこれらのサポートが追加される可能性があります）。
  * その他の制約は無視されます（そのまま残されます）。これにはSOSやインジケーター制約のような離散制約が含まれます。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x, Bin, start = 1);

julia> @variable(model, 1 <= y <= 10, Int, start = 2);

julia> @objective(model, Min, x + y);

julia> undo_relax = fix_discrete_variables(start_value, model);

julia> print(model)
Min x + y
Subject to
 x = 1
 y = 2

julia> undo_relax()

julia> print(model)
Min x + y
Subject to
 y ≥ 1
 y ≤ 10
 y integer
 x binary
```
