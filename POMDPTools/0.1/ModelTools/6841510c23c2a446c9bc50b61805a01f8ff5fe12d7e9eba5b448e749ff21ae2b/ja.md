```
ordered_observations(pomdp)
```

`obsindex(pomdp, a)`に従って順序付けられた観測の`AbstractVector`を返します。

`ordered_observations(mdp)`は常に、`observations(pomdp)`内のすべての観測を含む`AbstractVector{A}` `v`を返し、`obsindex(pomdp, v[i]) == i`となるように順序付けられています。効率のために、問題に応じてこれをオーバーライドすることを検討してもよいでしょう。
