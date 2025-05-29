```julia
evolution_operator(
    ed::KeldyshED.EDCore,
    grid::Keldysh.AbstractTimeGrid
) -> Vector{Keldysh.GenericTimeGF{ComplexF64, false}}

```

与えられたコンター時間グリッド上で進化演算子を計算します

$$
    \hat S(t, t') = \exp\left(-i \int_{t'}^{t} \hat H d\bar t\right)
$$

ハミルトニアン $\hat H$ の固有基底で表現されます。演算子は、$\hat H$ の不変部分空間に対応する対角ブロックのベクトル（行列値グリーン関数コンテナ）として返されます。
