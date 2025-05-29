```
add_method_initialize_zero_vars_default!(react::AbstractReaction, variables=PB.get_variables(react))
```

各タイムステップの開始時に変数をゼロに初期化するデフォルトメソッドを作成して追加します。デフォルトでは、`:initialize_to_zero`属性が`true`の`react`からすべての変数を追加します。

NB: TODO 変数はVarDepに変換されます（依存関係のチェックやソートは不要で、VarInitやそれに類似したものを定義できるかもしれません）。
