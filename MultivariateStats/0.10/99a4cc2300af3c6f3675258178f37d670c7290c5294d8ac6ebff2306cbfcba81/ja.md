```
cov_whitening(C)
```

共分散行列 `C` に基づいてホワイトニング変換係数行列 `W` を導出します。ここで、`C` は正方行列または `Cholesky` のインスタンスである可能性があります。

内部的に、この関数はコレスキー分解を使用してホワイトニング変換を解決します。理由は次のとおりです：$\mathbf{C} = \mathbf{U}^T \mathbf{U}$ とし、$\mathbf{W} = \mathbf{U}^{-1}$ とすると、$\mathbf{W}^T \mathbf{C} \mathbf{W} = \mathbf{I}$ となります。

**注意:** 戻り値の行列 `W` は上三角行列です。
