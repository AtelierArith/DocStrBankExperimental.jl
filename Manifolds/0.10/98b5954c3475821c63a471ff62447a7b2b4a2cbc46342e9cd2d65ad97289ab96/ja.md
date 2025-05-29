```
apply(A::QuaternionRotation, g::Quaternion, p)
```

点 `p` を群要素 `g` による共役を通じて [`Euclidean`](@ref)`(3)` 多様体から回転させます。式は次のようになります。

$$
(0, p_{rot,x}, p_{rot,y}, p_{rot,z}) = g ⋅ (0, p_x, p_y, p_z) ⋅ g^{\mathrm{H}}
$$

ここで、$(0, p_x, p_y, p_z)$ は点 `p` をエンコードする非実係数のクォータニオンであり、$g^{\mathrm{H}}$ は `g` のクォータニオン共役です。
