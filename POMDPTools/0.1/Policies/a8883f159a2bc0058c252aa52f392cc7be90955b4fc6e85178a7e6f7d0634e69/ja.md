```
showpolicy([io], [mime], m::MDP, p::Policy)
showpolicy([io], [mime], statelist::AbstractVector, p::Policy)
showpolicy(...; pre=" ")
```

`m` または `statelist` の状態と、それらの状態に対応するポリシー `p` のアクションを印刷します。

MDP バージョンの場合、`io[:limit]` が `true` の場合、表示を埋めるのに十分な状態のみを印刷します。
