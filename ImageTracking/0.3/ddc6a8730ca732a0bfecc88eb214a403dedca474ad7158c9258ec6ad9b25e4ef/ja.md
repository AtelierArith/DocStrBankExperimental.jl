```
evaluate_flow_error(ground_truth_flow, estimated_flow, EndpointError())
```

入力フローベクトルの次元に一致する2次元配列を返し、推定フローと真のフロー間のエンドポイントエラーを示します。

# 詳細

ある点での推定フローが(u0, v0)で、真のフローが(u1, v1)である場合、その点でのエラーはsqrt[(u0 - u1)^2 + (v0 - v1)^2]になります。

# 引数

フローパラメータは、各ピクセルの変位を表す長さ2のベクトル（SVector型）の2次元配列である必要があります。

# 例

2つのフロー間のエンドポイントエラーを計算します。

```julia

using ImageTracking

result = evaluate_flow_error(ground_truth_flow, estimated_flow, EndpointError())

imshow(result)
```

# 参考文献

[1] S. Baker, D. Scharstein, JP Lewis, S. Roth, M.J. Black, and R. Szeliski. A database and evaluation methodology for optical flow. International Journal of Computer Vision, 92(1):1–31, 2011.
