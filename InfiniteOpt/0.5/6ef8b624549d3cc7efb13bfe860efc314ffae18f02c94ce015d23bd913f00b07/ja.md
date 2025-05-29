```
JuMP.relax_integrality(model::InfiniteModel)::Function
```

`model`を修正して、すべてのバイナリおよび整数制約を変数から「緩和」します。具体的には、

  * バイナリ制約は削除され、変数が区間 $[0, 1]$ に制約されるように必要に応じて変数の境界が厳しくなります。
  * 整数制約は変数の境界を変更することなく削除されます。
  * その他のすべての制約は無視されます（そのまま残ります）。これには、SOSやインジケーター制約のような離散制約が含まれます。

元のモデルを復元するために引数なしで呼び出すことができる関数を返します。この関数の動作は、影響を受ける変数に対してその間に追加の変更が行われた場合には未定義です。

**例**

```julia-repl
julia> undo_relax = relax_integrality(model);

julia> print(model)
Min x + ∫{t ∈ [0, 10]}(y(t))
Subject to
 x ≥ 0.0
 y(t) ≥ 1.0
 x ≤ 1.0
 y(t) ≤ 10.0

julia> undo_relax()

julia> print(model)
Min x + ∫{t ∈ [0, 10]}(y(t))
Subject to
 y(t) ≥ 1.0
 y(t) ≤ 10.0
 y(t) integer
 x binary
```
