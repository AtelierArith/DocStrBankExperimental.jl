```
DiscreteBelief
```

確率ベクトルによって指定された信念。

`b` の正規化は一部の計算（例：pdf）で仮定されていますが、`update(...)` でのみ自動的に強制され、`DiscreteBelief(pomdp, b)` で不正に正規化された場合は警告が表示されます。

# コンストラクタ

```
DiscreteBelief(pomdp, b::Vector{Float64}; check::Bool=true)
```

# フィールド

  * `pomdp` : POMDP 問題
  * `state_list` : 順序付けられた状態のベクトル
  * `b` : 確率ベクトル
