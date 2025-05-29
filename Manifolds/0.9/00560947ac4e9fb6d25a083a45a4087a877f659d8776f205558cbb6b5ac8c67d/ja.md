```
hat(M::AbstractDecoratorManifold{𝔽,O}, ::Identity{O}, Xⁱ) where {𝔽,O<:AbstractGroupOperation}
```

与えられた基底 $e_i$ が [`Identity`](@ref) での接空間にあり、接成分ベクトル $X^i$ があるとき、次のように同等のベクトル表現を計算します ``X=X^i e_i**、ここでアインシュタインの総和記法が使用されます：

$$
∧ : X^i ↦ X^i e_i
$$

配列多様体の場合、これは接ベクトルのベクトル表現を配列表現に変換します。 [`vee`](@ref) マップは `hat` マップの逆です。
