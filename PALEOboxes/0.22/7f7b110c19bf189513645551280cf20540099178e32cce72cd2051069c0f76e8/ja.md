```
add_method_do_totals_default!(react::AbstractReaction, total_candidates=PB.get_variables(react);
    [filterfn] [, methodname] [, total_localnames] [, operatorID])
```

合計変数（スカラープロパティ）を追加するメソッドを作成して追加します。これは、`filterfn` に一致するコレクション `total_candidates` の変数に対して行われます（デフォルトでは、配列変数であり、属性 $:calc_total == true$ を持つものが対象となります）。

注：合計変数は、[`add_method_initialize_zero_vars_default!`](@ref) を使用してゼロに初期化する必要があります。
