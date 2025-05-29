```
ordered_states(mdp)
```

`stateindex(mdp, a)`に従って順序付けられた状態の`AbstractVector`を返します。

`ordered_states(mdp)`は常に、`states(mdp)`内のすべての状態を含む`AbstractVector{A}` `v`を返し、`stateindex(mdp, v[i]) == i`となるように順序付けられています。効率のために、問題に応じてこれをオーバーライドすることを検討してもよいでしょう。
