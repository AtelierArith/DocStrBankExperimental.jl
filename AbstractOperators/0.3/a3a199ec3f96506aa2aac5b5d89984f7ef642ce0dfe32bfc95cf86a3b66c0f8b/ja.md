`Sigmoid([domainType=Float64::Type,] dim_in::Tuple, γ = 1.)`

入力次元 `dim_in` を持つシグモイド非線形演算子を作成します。

$$
\sigma(\mathbf{x}) = \frac{1}{1+e^{-\gamma \mathbf{x} } }
$$
