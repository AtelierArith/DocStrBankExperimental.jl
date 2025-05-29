`SoftMax([domainType=Float64::Type,] dim_in::Tuple)`

入力次元 `dim_in` を持つソフトマックス非線形演算子を作成します。

$$
\sigma(\mathbf{x}) = \frac{e^{\mathbf{x} }}{ \sum e^{\mathbf{x} } }
$$
