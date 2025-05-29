`struct RK_W3 <: ReproducingKernel_3`

Sobolev空間$W^2_3 [0,1]$の再生核の型を定義します：

$$
V(\eta, \xi) =
  \begin{cases}
       \sum_{i=0}^2 \frac{\xi^i}{!i} \left ( \frac{\eta^i}{!i} + (-1)^{i} \frac {\eta^{5 - i}}{(5 - i)!}  \right )  \,  , &  0 \le \eta \le \xi \le 1
        \\
       \sum_{i=0}^2 \frac{\eta^i}{!i} \left ( \frac{\xi^i}{!i} + (-1)^{i} \frac {\xi^{5 - i}}{(5 - i)!}  \right ) \,  , &  0 \le \xi \le \eta \le 1   \end{cases}
$$
