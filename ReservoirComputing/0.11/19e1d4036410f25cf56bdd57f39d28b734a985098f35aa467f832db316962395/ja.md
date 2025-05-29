```
StandardRidge([Type], [reg])
```

リッジ回帰に基づく`train`のためのトレーニングメソッドを返します。リッジ回帰の方程式は次のとおりです：

$$
\mathbf{w} = (\mathbf{X}^\top \mathbf{X} + 
\lambda \mathbf{I})^{-1} \mathbf{X}^\top \mathbf{y}
$$

# 引数

  * `Type`: 正則化引数のタイプ。デフォルトは内部で推測され、通常はこれを調整する必要はありません。
  * `reg`: 正則化係数。デフォルトは0.0（線形回帰）に設定されています。

```
