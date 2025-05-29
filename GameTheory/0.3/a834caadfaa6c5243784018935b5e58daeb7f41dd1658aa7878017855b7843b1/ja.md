```
is_pareto_efficient(g, action_profile)
```

ゲーム `g` に対して `action_profile` がパレート効率である場合は true を返します。

# 引数

  * `g::NormalFormGame` : N人のノーマルフォームゲームのインスタンス。
  * `action_profile::PureActionProfile` : N 個の整数のタプル（純粋なアクション）。

# 戻り値

  * `::Bool`

```
