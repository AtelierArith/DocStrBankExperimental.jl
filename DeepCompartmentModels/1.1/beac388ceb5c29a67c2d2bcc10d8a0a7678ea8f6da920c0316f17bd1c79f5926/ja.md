```
interpret_branch(model, covariate_idx, anchor; x)
```

AbstractModelインターフェースに従ったモデルの解釈関数を実行するための便利な関数です。

# 引数:

  * `model::AbstractModel`: Multi-branchベースのニューラルネットワークを使用するAbstractModel（例: DeepCompartmentModel(...)）。
  * `covariate_idx`: 入力ベクトル内の共変量のインデックス。
  * `anchor`: 出力が「アンカー」される非正規化共変量値、すなわち f(anchor) = 1。
  * `x`: ブランチへの正規化されたダミー入力。
