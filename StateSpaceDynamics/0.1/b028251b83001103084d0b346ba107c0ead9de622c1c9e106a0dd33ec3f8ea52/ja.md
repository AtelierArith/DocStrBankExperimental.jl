```
gaussian_entropy(H::Symmetric{T}) where T <: Real
```

ヘッセ行列（すなわち負の精度）行列 `H` を持つガウス分布のエントロピーを計算します。

# 引数

  * `H::Symmetric{T}`: ヘッセ行列。

# 戻り値

  * ガウス分布のエントロピー。
