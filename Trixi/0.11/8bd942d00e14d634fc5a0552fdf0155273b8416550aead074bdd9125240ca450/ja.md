```
MaxwellEquations1D(c = 299_792_458.0)
```

電磁力学のマクスウェル方程式

$$
\frac{\partial}{\partial t}
\begin{pmatrix}
E \\ B
\end{pmatrix}
+ 
\frac{\partial}{\partial x}
\begin{pmatrix}
c^2 B \\ E
\end{pmatrix}
=
\begin{pmatrix}
0 \\ 0 
\end{pmatrix}
$$

光速 `c = 299792458 m/s`（真空中）での1次元の方程式です。1次元では、マクスウェル方程式は波動方程式に簡略化されます。直交する磁場（例：`B_y`）と電場（`E_z`）は、`x`方向に波として領域を伝播します。参考として、以下を参照してください。

  * 例：数値解析法の保存法則に関する方法：分析からアルゴリズムへ p.15 https://doi.org/10.1137/1.9781611975109
  * または、https://inria.hal.science/hal-01720293/document の式（1）
