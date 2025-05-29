`struct RK_W1 <: ReproducingKernel_1`

Define a type of reproducing kernel of Sobolev space $W^2_1 [0,1]$:

$$
V(\eta, \xi) =
  \begin{cases}
       1 + \eta \,  , &  0 \le \eta \le \xi \le 1 \\
       1 + \xi \,  , &  0 \le \xi \le \eta \le 1
    \end{cases}
$$
