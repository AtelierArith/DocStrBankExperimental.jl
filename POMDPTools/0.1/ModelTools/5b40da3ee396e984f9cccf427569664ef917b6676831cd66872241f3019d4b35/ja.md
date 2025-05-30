```
ordered_actions(mdp)
```

`actionindex(mdp, a)`に従って順序付けられたアクションの`AbstractVector`を返します。

`ordered_actions(mdp)`は常に、`actions(mdp)`内のすべてのアクションを含む`AbstractVector{A}` `v`を返し、`actionindex(mdp, v[i]) == i`となるように順序付けられています。効率のために、問題に応じてこれをオーバーライドすることを検討してもよいでしょう。
