```
Greedy(m::Int, s::Int)
```

  * `m` は希望する誘導点の数です
  * `s` は新しい誘導点を選択するためのミニバッチサイズです

GreedyアプローチはTitsiasによって最初に提案されました[1]。アルゴリズムはデータのミニバッチをループし、最良のELBO改善を選択します。`inducingpoints`に出力`y`、`kernel`、および`noise`をキーワード引数として渡す必要があります。

[1] Titsias, M. Variational Learning of Inducing Variables in Sparse Gaussian Processes. Aistats 5, 567–574 (2009). ```
