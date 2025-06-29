```
hat(M::AbstractManifold, p, Xⁱ)
```

点 `p` における接空間の基底 $e_i$ と接成分ベクトル $X^i ∈ ℝ$ が与えられたとき、アインシュタインの総和記法を用いて、同等のベクトル表現 $X=X^i e_i$ を計算します：

$$
∧ : X^i ↦ X^i e_i
$$

配列多様体の場合、これは接ベクトルのベクトル表現を配列表現に変換します。[`vee`](@ref) マップは `hat` マップの逆です。
