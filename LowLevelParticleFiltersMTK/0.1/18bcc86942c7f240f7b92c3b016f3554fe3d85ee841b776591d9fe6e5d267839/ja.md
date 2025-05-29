```
EstimatedOutput(kf, prob, sym)
```

出力関数を作成します。この関数は次のように呼び出すことができます。

```
g(x::Vector,    u, p, t)     # 出力を計算する
g(xR::MvNormal, u, p, t)     # 入力分布 xR に基づいて出力分布を計算する
g(kf,           u, p, t)     # AbstractKalmanFilter の現在の状態に基づいて出力分布を計算する
```

# 引数:

  * `kf`: カルマン型フィルタ
  * `prob`: `StateEstimationProblem` オブジェクト
  * `sym`: 関数が出力すべき象徴的な式または象徴的な式のベクトル。
