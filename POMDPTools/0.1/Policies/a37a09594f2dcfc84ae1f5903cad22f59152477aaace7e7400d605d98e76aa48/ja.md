```
 ValueDictPolicy(mdp)
```

状態-行動ペアのQ値を格納する`Dict`で構成される一般的なMDPポリシーです。デフォルト値よりも高いエントリがない場合、これはデフォルトポリシーにフォールバックします。

# キーワード引数

  * `value_table::AbstractDict` 値辞書、キーは(s, a)タプルです。
  * `default_value::Float64` `value_dict`のデフォルト値。
  * `default_policy::Policy` どのアクションも`default_value`より高い値を持たない場合に取られるポリシー。
