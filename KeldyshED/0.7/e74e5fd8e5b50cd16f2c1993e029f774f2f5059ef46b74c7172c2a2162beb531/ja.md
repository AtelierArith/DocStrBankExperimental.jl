```julia
density_matrix(ed::KeldyshED.EDCore, β::Real) -> Vector

```

逆温度 $\beta$ における平衡密度行列 $\hat\rho = e^{-\beta\hat H} / Z$ を、ハミルトニアン $\hat H$ の固有基底で表現します。密度行列は、$\hat H$ の不変部分空間に対応する対角ブロックのベクトルとして返されます。
