```
epsilon_net(X, ϵ; metric)
```

点群 X を半径 ϵ のボールで覆います。ボールの中心である X のインデックスのベクトルを返します。

## 詳細

最初に X の最初の点を ϵ-ボールで覆います。次に、このボールで覆われていない X の次の点を探します。このプロセスを繰り返し、すべての点がボールの中に入るまで続けます。
