```
planar_symmetric_qubit_kets( n :: Int64 ) :: Vector{Ket{Float64}}
```

$$
x-z
$$

平面で対称的に配置された`n`個の`Ket`のセットを構築します。各ketは`2π/n`のブロッホ角で分離されています。`Ket`は次の形式で構築されます：

$$
|\psi_j \rangle = \cos(j \pi/n) | 0\rangle + \sin(j \pi/n)|1\rangle
$$

ここで、$j \in \{0,\cdots, (n-1)\}$です。

`n < 2`の場合、`DomainError`がスローされます。
