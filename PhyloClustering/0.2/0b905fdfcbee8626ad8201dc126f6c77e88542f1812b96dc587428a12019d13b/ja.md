```
distance(tree::AbstractMatrix{<:Real})
```

ツリー行列の距離行列を取得します [`split_weight`](@ref) によって返されます。

# 引数

  * `tree`: B * N ツリー行列（ツリー行列の各列は二分割形式のB次元ツリーです）。

# 出力

[`hc_label`](@ref) の入力となるペアワイズ距離 `Matrix`。
