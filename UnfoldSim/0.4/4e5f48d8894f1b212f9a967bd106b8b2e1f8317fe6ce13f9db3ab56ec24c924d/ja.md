```
MultiSubjectDesign <: AbstractDesign
```

複数の被験者の実験デザインを指定するための型（与えられたランダム効果構造に基づく）。

ヒント: [`generate_events`](@ref) 関数を使用して結果のデータフレームを確認してください。 `n_items` のアイテム数は、アイテム間レベルの数の倍数である必要があります。このサンプルは `n_subjects` と被験者間レベルの数に適用されます。

# フィールド

  * `n_subjects::Int`: 被験者の数。
  * `n_items::Int`: アイテム/刺激の数（時には ≈ 試行）。
  * `subjects_between::Dict{Symbol,Vector}`: 被験者間の効果、例: 若者 vs 高齢者。
  * `items_between::Dict{Symbol,Vector}`: アイテム間の効果、例: 自然画像 vs 人工画像（ただし、`subjects_between` にも指定されていない場合はすべての被験者に表示される）。
  * `both_within::Dict{Symbol,Vector}`: 完全に交差した効果、すなわち被験者内およびアイテム内の条件/共変量。
  * `event_order_function = (rng, x) -> x`: イベントをソートまたはシャッフルするために使用できます。例: `(rng, x) -> shuffle(rng, x)`（または短く `event_order_function = shuffle`）。デフォルトは同一関数であり、すなわちイベントの順序を変更しません。

# 例

```julia-repl
# 被験者間およびアイテム間の同じ条件を宣言すると、完全な被験者/アイテム間デザインが得られます。
julia> design = MultiSubjectDesign(;
                       n_items = 10,
                       n_subjects = 30,
                       subjects_between = Dict(:cond => ["levelA", "levelB"]),
                       items_between = Dict(:cond => ["levelA", "levelB"]),
                       )
MultiSubjectDesign
  n_subjects: Int64 30
  n_items: Int64 10
  subjects_between: Dict{Symbol, Vector}
  items_between: Dict{Symbol, Vector}
  both_within: Dict{Symbol, Vector}
  event_order_function: #3 (function of type UnfoldSim.var"#3#7")

julia> generate_events(StableRNG(1), design)
150×3 DataFrame
 Row │ subject  cond    item   
     │ String   String  String 
─────┼─────────────────────────
   1 │ S01      levelA  I01
   2 │ S01      levelA  I03
   3 │ S01      levelA  I05
  ⋮  │    ⋮       ⋮       ⋮
 148 │ S30      levelB  I06
 149 │ S30      levelB  I08
 150 │ S30      levelB  I10
               144 rows omitted
```

さらに [`SingleSubjectDesign`](@ref)、[`RepeatDesign`](@ref) を参照してください。
