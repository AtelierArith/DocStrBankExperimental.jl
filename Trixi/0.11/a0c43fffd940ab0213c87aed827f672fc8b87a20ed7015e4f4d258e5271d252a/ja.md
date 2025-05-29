```
CompressibleEulerMulticomponentEquations2D(; gammas, gas_constants)
```

圧縮性オイラー方程式の多成分バージョン

$$
\frac{\partial}{\partial t}
\begin{pmatrix}
\rho v_1 \\ \rho v_2 \\ \rho e \\ \rho_1 \\ \rho_2 \\ \vdots \\ \rho_{n}
\end{pmatrix}
+
\frac{\partial}{\partial x}
\begin{pmatrix}
\rho v_1^2 + p \\ \rho v_1 v_2 \\ ( \rho e +p) v_1 \\ \rho_1 v_1 \\ \rho_2 v_1 \\ \vdots \\ \rho_{n} v_1
\end{pmatrix}
+
\frac{\partial}{\partial y}
\begin{pmatrix}
\rho v_1 v_2 \\ \rho v_2^2 + p \\ ( \rho e +p) v_2 \\ \rho_1 v_2 \\ \rho_2 v_2 \\ \vdots \\ \rho_{n} v_2
\end{pmatrix}
=
\begin{pmatrix}
0 \\ 0 \\ 0 \\ 0 \\ 0 \\ \vdots \\ 0
\end{pmatrix}
$$

二次元空間における熱的に完璧な気体の場合。ここで、$\rho_i$は成分$i$の密度、$\rho=\sum_{i=1}^n\rho_i$は個々の$\rho_i$の合計、$v_1$, $v_2$は速度、$e$は特定の総エネルギー**ではなく**特定の内部エネルギーであり、

$$
p = (\gamma - 1) \left( \rho e - \frac{1}{2} \rho (v_1^2 + v_2^2) \right)
$$

圧力、

$$
\gamma=\frac{\sum_{i=1}^n\rho_i C_{v,i}\gamma_i}{\sum_{i=1}^n\rho_i C_{v,i}}
$$

全体の比熱比、$\gamma_i$は成分$i$の比熱比、

$$
C_{v,i}=\frac{R}{\gamma_i-1}
$$

成分$i$の定積比熱。

成分が1つ以上ある場合、比熱比`gammas`と気体定数`gas_constants`は[kJ/(kg*K)]のタプルとして渡す必要があります。例えば、`gammas=(1.4, 1.667)`のように。

残りの変数、例えば定積比熱`cv`や定圧比熱`cp`は、熱的に完璧な気体を考慮して計算されます。
