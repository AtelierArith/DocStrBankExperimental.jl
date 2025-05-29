```
Move{A<:Action,P<:Policy,V<:AbstractArray,T<:AbstractFloat}
```

モンテカルロ移動を表す構造体で、関連するアクション、ポリシー、およびパラメータを持ちます。

# フィールド

  * `action::A`: 移動で実行されるアクション
  * `policy::P`: アクションを提案するために使用されるポリシー
  * `parameters::V`: ポリシーのパラメータ
  * `weight::T`: スイープでこの移動を選択する重み/確率
  * `total_calls::Int`: この移動が試みられた回数の合計
  * `accepted_calls::Int`: この移動が受け入れられた回数

# 型パラメータ

  * `A`: アクションの型
  * `P`: ポリシーの型
  * `V`: パラメータ配列の型
  * `T`: 重みの型（浮動小数点）
