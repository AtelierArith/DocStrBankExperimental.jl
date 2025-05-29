```
calculate_statistics(error)
```

フローエラーを平均と標準偏差、さらに「ロバスト性」を測定する2つの追加統計量で定量化します。

# 詳細

RXとAXはロバスト性統計です。RXは、エラーメジャーがXを超えるピクセルの割合を示します。AXは、Xパーセンタイルでのエラーメジャーの精度を示します。

# 引数

エラーパラメータは、2つのフロー間のエラーを表す長さ2のベクトル（SVector型）の2次元配列である必要があります。

# 例

エンドポイントエラーメソッドを使用して計算されたフローエラーの平均、SD、RX、AX統計を計算します。

```julia

using ImageTracking

error = evaluate_flow_error(ground_truth_flow, estimated_flow, EndpointError())
mean, sd, rx, ax = calculate_statistics(error)
```

角度エラーメソッドを使用して計算されたフローエラーの平均、SD、RX、AX統計を計算します。

```julia

using ImageTracking

error = evaluate_flow_error(ground_truth_flow, estimated_flow, AngularError())
mean, sd, rx, ax = calculate_statistics(error)
```

# 参考文献

[1] S. Baker, D. Scharstein, JP Lewis, S. Roth, M.J. Black, and R. Szeliski. A database and evaluation methodology for optical flow. International Journal of Computer Vision, 92(1):1–31, 2011.
