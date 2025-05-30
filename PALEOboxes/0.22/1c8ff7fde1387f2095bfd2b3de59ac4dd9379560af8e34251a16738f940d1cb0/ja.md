```
show_variables(domain::Domain; [attributes], [filter], showlinks=false, modeldata=nothing) -> DataFrame
```

ドメイン変数のテーブルを表示します。オプションで変数リンクやデータを取得します。

# キーワード:

  * `attributes=[:units, :vfunction, :space, :field_data, :description]`: 表示する変数属性
  * `showlinks=false`: このドメイン変数にリンクする[`VariableReaction`](@ref)を表示するにはtrueに設定します。
  * `modeldata=nothing`: 変数の値も表示するように設定します。
  * `filter=attrb->true`: 変数属性でフィルタリングするための関数。例: `filter=attrb->attrb[:vfunction]!=PB.VF_Undefined`は状態変数と導関数を表示します。
