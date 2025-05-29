```
inner(::SymplecticGrassmann, p, X, Y)
```

Riemannian内積$g^{\mathrm{SpGr}}_p(X,Y)$を[`SymplecticGrassmann`](@ref)多様体`\mathrm{SpGr}`上で計算します。

$$
p
$$

が[`SymplecticStiefel`](@ref)多様体上の点で表され、その同値類の代表として作用し、接ベクトル$X,Y \in \mathrm{Hor}_p^π\operatorname{SpSt}(2n,2k)$が水平接ベクトルである場合を考えます。

このとき、内積は命題補題4.8 [BendokatZimmermann:2021](@cite)に従って次のように表されます。

$$
g^{\mathrm{SpGr}}_p(X,Y) = \operatorname{tr}\bigl(
        (p^{\mathrm{T}}p)^{-1}X^{\mathrm{T}}(I_{2n} - pp^+)Y
    \bigr),
$$

ここで、$I_{2n}$は単位行列を示し、$(⋅)^+$は[`symplectic_inverse`](@ref)です。 ```
