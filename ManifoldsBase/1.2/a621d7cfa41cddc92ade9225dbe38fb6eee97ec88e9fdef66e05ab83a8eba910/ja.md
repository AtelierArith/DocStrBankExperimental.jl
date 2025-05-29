```
ODEExponentialRetraction{T<:AbstractRetractionMethod, B<:AbstractBasis} <: AbstractRetractionMethod
```

マニフォールド上の指数写像を、与えられたマニフォールドのデフォルト接続を仮定して、常微分方程式を解くことによって、測地線を記述するODEを1で評価することによって近似します。

$$
\frac{d^2}{dt^2} p^k + Γ^k_{ij} \frac{d}{dt} p_i \frac{d}{dt} p_j = 0,
$$

ここで、$Γ^k_{ij}$は第二種のクリストッフェル記号であり、アインシュタインの総和規約が仮定されています。

# コンストラクタ

```
ODEExponentialRetraction(
    r::AbstractRetractionMethod,
    b::AbstractBasis=DefaultOrthogonalBasis(),
)
```

内部で使用するための再tractionを生成し（いくつかのアプローチ用）、接空間の基底を指定します。
