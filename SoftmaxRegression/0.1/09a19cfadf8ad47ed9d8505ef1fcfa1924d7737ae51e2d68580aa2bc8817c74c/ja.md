inputs (required):      X: デザイン行列、グローバルインターセプトが含まれていると仮定（1の列）

```
y: ターゲットクラスラベル
```

inputs (optional):      verbose: 最適化の成功または失敗が出力されるかどうかを決定するブール値

outputs:     推定されたインターセプトと係数行列のタプル:       res = softmax_regression(X, y)      res.intercepts # 推定されたインターセプトにアクセスするため      res.betas # 係数行列にアクセスするため
