```
generalized_bell_kets( dim :: Int64 ) :: Vector{Ket{Float64}}
```

エンタングルされた二部量子状態のベル基底で、各状態の次元は `dim` です。各状態は次のように構築されます。

$$
|\Psi^p_c\rangle = \frac{1}{\sqrt{d}}\sum_{j=0}^{d-1} e^{i2\pi pj/d}|j\rangle |\mod(j+c,d)\rangle
$$

ここで、$p,c\in \{0,\cdots, (d-1)\}$ であり、$d$ は `dim` です。繰り返し処理されると、$c$ は主要インデックスで、$p$ は副次インデックスです。

`dim ≥ 2` が満たされない場合、`DomainError` がスローされます。
