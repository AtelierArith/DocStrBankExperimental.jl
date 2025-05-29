```julia
DiffEqBase.NonlinearProblem(rs::ReactionSystem, u0,
        p = DiffEqBase.NullParameters(), args...;
        name = nameof(rs), combinatoric_ratelaws = get_combinatoric_ratelaws(rs),
        remove_conserved = false, checks = false, check_length = false, 
        structural_simplify = remove_conserved, all_differentials_permitted = false, 
        kwargs...)
```

[`ReactionSystem`](@ref)を`ModelingToolkit.NonlinearSystem`に変換します。

キーワード引数とデフォルト値：

  * `combinatoric_ratelaws=true`は、レート法則を計算する際に階乗スケーリング因子を使用します。つまり、`2S -> 0`のレート`k`の場合、レート法則は`k*S^2/2!`になります。`combinatoric_ratelaws=false`に設定すると、レート法則は`k*S^2`になり、スケーリング因子は無視されます。デフォルトは、`ReactionSystem`が構築されたときに与えられた値（デフォルトはtrue）です。
  * `remove_conserved=false`、`true`に設定すると、基礎となる反応のセットの保存則を計算します（結合されたODEや代数方程式は無視されます）。各保存則に対して、1つの定常状態方程式が排除され、保存則に置き換えられます。これにより、非特異的なヤコビ行列が確保されます。このオプションを使用する場合は、変換されたシステムに対して`ModelingToolkit.structural_simplify`を呼び出して、システム方程式から保存則を排除することをお勧めします。
  * `conseqs_remake_warn = true`、`false`に設定すると、`remake`と保存則に関する警告を無効にします。詳細については、[FAQエントリ](https://docs.sciml.ai/Catalyst/stable/faqs/#faq_remake_nonlinprob)を参照してください。
  * `expand_catalyst_funs = true`、Catalystで定義された関数（例：`hill(A,B,C,D)`）を別のシステムタイプに変換する際に、その有理関数表現に置き換えます。`false`に設定すると無効になります。
