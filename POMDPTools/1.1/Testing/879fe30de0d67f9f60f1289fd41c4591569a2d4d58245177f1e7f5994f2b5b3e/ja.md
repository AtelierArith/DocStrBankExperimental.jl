```
has_consistent_distributions(m::MDP; atol=0)
has_consistent_distributions(m::POMDP; atol=0)
```

離散問題の分布に問題が見つからない場合はtrueを返します。問題が見つかった場合は情報を印刷し、falseを返します。

以下をテストします：

  * すべての確率が正であること
  * すべての分布の確率が1に合計されること
  * 正の確率を持つすべての項目がサポート内にあること

# キーワード引数

  * `atol`: すべての確率チェックに対して`approx`に渡される絶対許容誤差
