```
pure2mixed(num_actions, action)
```

純粋なアクションを対応する混合アクションに変換します。

# 引数

  * `num_actions::Integer` : 純粋なアクションの数（＝混合アクションの長さ）。
  * `action::PureAction` : 対応する混合アクションに変換する純粋なアクション。

# 戻り値

  * `mixed_action::Vector{Float64}` : 与えられた純粋なアクションの混合アクション表現。
