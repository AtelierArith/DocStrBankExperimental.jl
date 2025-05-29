```
exp(M::Grassmann, p::ProjectorPoint, X::ProjectorTVector)
```

[`Grassmann`](@ref)上の指数写像を次のように計算します。

$$
    \exp_pX = \operatorname{Exp}([X,p])p\operatorname{Exp}(-[X,p]),
$$

ここで、$\operatorname{Exp}$は行列の指数関数を示し、$[A,B] = AB-BA$は行列のコマドゥータを示します。

詳細については、[BendokatZimmermannAbsil:2020](@cite)の命題3.2を参照してください。
