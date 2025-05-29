```
expand_all_measures!(model::InfiniteModel)::Nothing
```

`model`の目的関数および/または制約に使用されるすべての測度を展開します。目的関数と制約はそれに応じて更新されます。展開を受け入れるために必要に応じて変数がモデルに追加されることに注意してください（すなわち、ポイント変数と半無限変数が必要に応じて作成されます）。測度データおよび/または測度式に対して展開が未定義の場合はエラーが発生します。

これは、カスタムオプティマイザーモデルを使用する拡張にとって便利です。なぜなら、`model`が新しいモデルに変換される前に測度を評価するために使用できるからです。このメソッドは、[`expand_measure`](@ref)を拡張することでカスタム測度データ型を処理するように拡張することもできます。このメソッドは、[`expand_measures`](@ref)を介して`expand_measure`を活用します。オプションとして、特定のケースで解析的展開が可能な場合に[`is_analytic`](@ref)によってトリガーされる[`analytic_expansion`](@ref)も拡張できます。

**例**

```julia-repl
julia> print(model)
Min integral{t ∈ [0, 6]}[g(t)*t] + z
Subject to
 T(t, x) ≥ 0.0, ∀ t ∈ [0, 6], xi ∈ [-1, 1]
 z ≥ 0.0
 g(t) + z ≥ 42.0, ∀ t ∈ [0, 6]
 integral{t ∈ [0, 6]}[T(t, x)] ≥ 0.0, ∀ x ∈ [-1, 1]

julia> expand_all_measures!(model)

julia> print(model)
Min 3 g(6) + z
Subject to
 T(t, x) ≥ 0.0, ∀ t ∈ [0, 6], xi ∈ [-1, 1]
 z ≥ 0.0
 g(t) + z ≥ 42.0, ∀ t ∈ [0, 6]
 0.5 T(0, x) + 0.5 T(6, xi) ≥ 0.0, ∀ x ∈ [-1, 1]
```
