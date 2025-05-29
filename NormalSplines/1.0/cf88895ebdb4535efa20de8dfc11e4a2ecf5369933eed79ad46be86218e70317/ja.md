`struct RK_W2 <: ReproducingKernel_2`

Sobolev空間$W^2_2 [0,1]$の再生核の型を定義します：

$$
V(\eta, \xi) =
  \begin{cases}
       1 + (\eta + \eta^2 / 2)\xi - \eta^3 / 6  \,  , &  0 \le \eta \le \xi \le 1  \\
       1 + (\xi + \xi^2 / 2)\eta - \xi^3 / 6 \,  , &  0 \le \xi \le \eta \le 1
    \end{cases}
$$
