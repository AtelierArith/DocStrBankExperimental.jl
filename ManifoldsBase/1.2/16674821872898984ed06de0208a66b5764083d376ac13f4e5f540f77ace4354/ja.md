```
DifferentiatedRetractionVectorTransport{R<:AbstractRetractionMethod} <:
    AbstractVectorTransportMethod
```

リトラクションを微分することによって与えられるベクトル輸送を指定する型です。これは二つの方法で導入できます。$\mathcal M$をリーマン多様体、$p∈\mathcal M$を点、$X,Y∈ T_p\mathcal M$を$p$における二つの接ベクトルとします。

リトラクション（cf. [`AbstractRetractionMethod`](@ref)）$\operatorname{retr}$が与えられたとき、`X`の`Y`方向のベクトル輸送（cf. [`vector_transport_direction`](@ref)）は、このリトラクションを微分することによって与えられ、

$$
\mathcal T^{\operatorname{retr}}_{p,Y}X
= D_Y\operatorname{retr}_p(Y)[X]
= \frac{\mathrm{d}}{\mathrm{d}t}\operatorname{retr}_p(Y+tX)\Bigr|_{t=0}.
$$

詳細については[AbsilMahonySepulchre:2008](@cite)のセクション8.1.2を参照してください。

これは、$q=\operatorname{retr}_pX$を導入し、次のように定義することによって、[`vector_transport_to`](@ref)として同様に表現できます。

$$
\mathcal T^{\operatorname{retr}}_{q \gets p}X = \mathcal T^{\operatorname{retr}}_{p,Y}X
$$

これは実際には、$Y = \operatorname{retr}_p^{-1}q$を計算するために[`inverse_retract`](@ref)が存在する必要があります。

# コンストラクタ

```
DifferentiatedRetractionVectorTransport(m::AbstractRetractionMethod)
```
