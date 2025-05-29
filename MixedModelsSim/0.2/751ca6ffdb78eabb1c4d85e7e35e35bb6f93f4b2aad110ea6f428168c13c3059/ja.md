```
simdat_crossed([RNG], subj_n, item_n;
               subj_btwn=nothing, item_btwn=nothing, both_win=nothing,
               subj_prefix="S", item_prefix="I")
```

行テーブルを返します。デザインは以下によって指定されます：

  * 被験者の数（`subj_n`）、
  * アイテムの数（`item_n`）
  * 被験者間要因（`subj_btwn`）
  * アイテム間要因（`item_btwn`）
  * 被験者内/アイテム要因（`both_win`）

要因が被験者間およびアイテム間の両方である場合、同じキーと同じレベルで`subj_btwn`と`item_btwn`の両方に配置します。

要因は以下の形式の辞書として指定する必要があります：

```julia
Dict(
    :factor1_name => ["F1_level1", "F1_level2"],
    :factor2_name => ["F2_level1", "F2_level2", "F2_level3"]
)
```

デザインに加えて、行テーブルには、さらなるデザインのシミュレーションの基礎としてN(0,1)ノイズで事前に入力されたフィールド`dv`が含まれます。

!!! 注     被験者/アイテムの数は、被験者間/アイテム間要因レベルの組み合わせの数で割り切れる必要があります。言い換えれば、この関数はバランスの取れたデザインを前提としており、それが不可能な場合はエラーをスローします。
