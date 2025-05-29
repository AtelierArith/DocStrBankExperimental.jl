```
 ValuePolicy{P<:Union{POMDP,MDP}, T<:AbstractMatrix{Float64}, A}
```

値テーブルで構成される一般的なMDPポリシー。`stateindex(mdp, s)`のエントリは、状態`s`で取られるアクションです。値テーブル内のアクションの順序は、`act`内のアクションの順序と一致していることが期待されます。`act`が構築時に明示的に設定されていない場合、`act`は`actionindex`に従って順序付けられます。

# フィールド

  * `mdp::P` MDP問題
  * `value_table::T` |S|x|A|行列としての値テーブル
  * `act::Vector{A}` 可能なアクション
