`struct RK_W2 <: ReproducingKernel_2`

Define a type of reproducing kernel of Sobolev space $W^2_2 [0,1]$:

$$
V(\eta, \xi) =
  \begin{cases}
       1 + (\eta + \eta^2 / 2)\xi - \eta^3 / 6  \,  , &  0 \le \eta \le \xi \le 1  \\
       1 + (\xi + \xi^2 / 2)\eta - \xi^3 / 6 \,  , &  0 \le \xi \le \eta \le 1
    \end{cases}
$$
