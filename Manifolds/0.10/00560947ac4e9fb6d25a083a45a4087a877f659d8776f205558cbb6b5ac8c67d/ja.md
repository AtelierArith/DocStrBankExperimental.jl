```
hat(M::AbstractDecoratorManifold{𝔽,O}, ::Identity{O}, Xⁱ) where {𝔽,O<:AbstractGroupOperation}
```

与えられた基底 $e_i$ が [`Identity`](@ref) における接空間上にあり、接成分ベクトル $X^i$ があるとき、同等のベクトル表現 $X=X^i e_i$ を計算します。ここで、アインシュタインの総和記法が使用されます：

$$
∧ : X^i ↦ X^i e_i
$$

配列多様体の場合、これは接ベクトルのベクトル表現を配列表現に変換します。[`vee`](@ref) マップは `hat` マップの逆です。
