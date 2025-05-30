```
transition_matrix(p::SparseTabularProblem, a)
```

スパースタブラー問題の遷移モデルのアクセサ関数です。アクション a を取るときの遷移確率を含むスパース行列を返します: T[s, sp] = Pr(sp | s, a)。
