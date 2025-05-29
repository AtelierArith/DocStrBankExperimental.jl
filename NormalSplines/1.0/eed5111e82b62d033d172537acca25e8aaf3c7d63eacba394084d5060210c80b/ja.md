`struct RK_W1 <: ReproducingKernel_1`

Sobolev空間$W^2_1 [0,1]$の再生核の型を定義します：

$$
V(\eta, \xi) =
  \begin{cases}
       1 + \eta \,  , &  0 \le \eta \le \xi \le 1 \\
       1 + \xi \,  , &  0 \le \xi \le \eta \le 1
    \end{cases}
$$
