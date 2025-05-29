```
interpret_branch(model, covariate_idx, anchor, ps, st; x)
```

特定のブランチの出力をダミー入力に基づいて返します。共変量の効果を解釈するために使用できます。正規化されていない `x` と、`anchor` の位置での予測で割ったブランチ出力 `y` を返します：

```julia
y = f(x) ./ f(anchor)
```

# 引数:

  * `ann`: Lux モデル。
  * `ps`: モデルパラメータ。
  * `st`: モデル状態。
  * `covariate_idx`: 入力ベクトル内の共変量のインデックス。
  * `anchor`: 出力が「アンカー」される正規化されていない共変量値、すなわち f(anchor) = 1。
  * `x`: ブランチへの正規化されたダミー入力。
