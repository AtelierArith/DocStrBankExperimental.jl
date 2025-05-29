```
アクティビティ
```

学習者が実行し、応答するための単一のアクティビティ。アクティビティはAnattaにおける学習の基本単位です。それは...

# フィールド

  * `prompt`	: 学習者によるアクティビティを促すテキスト。
  * `hint`	: プロンプトに応答する方法を学習者に示唆するテキスト。
  * `success`	: 成功した学習者の応答の基準を定義するブール関数。

# 例

```julia
julia> act = Anatta.Activity( "What is 2+3?", "Add the numbers together", x -> x==5)
Anatta.Activity("What is 2+3?", "Add the numbers together", var"#5#6"())

julia> act.success(5)
true
```
