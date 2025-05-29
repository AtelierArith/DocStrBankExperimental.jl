```
CompressibleEulerMulticomponentEquations1D(; gammas, gas_constants)
```

圧縮性オイラー方程式の多成分バージョン

$$
\frac{\partial}{\partial t}
\begin{pmatrix}
\rho v_1 \\ \rho e \\ \rho_1 \\ \rho_2 \\ \vdots \\ \rho_{n}
\end{pmatrix}
+
\frac{\partial}{\partial x}
\begin{pmatrix}
\rho v_1^2 + p \\ (\rho e +p) v_1 \\ \rho_1 v_1 \\ \rho_2 v_1 \\ \vdots \\ \rho_{n} v_1
\end{pmatrix}

=
\begin{pmatrix}
0 \\ 0 \\ 0 \\ 0 \\ \vdots \\ 0
\end{pmatrix}
$$

一つの空間次元における熱的に完璧な気体の場合。ここで、$\rho_i$は成分$i$の密度、$\rho=\sum_{i=1}^n\rho_i$は個々の$\rho_i$の合計、$v_1$は速度、$e$は特定の総エネルギー**ではなく**特定の内部エネルギー、そして

$$
p = (\gamma - 1) \left( \rho e - \frac{1}{2} \rho v_1^2 \right)
$$

は圧力、

$$
\gamma=\frac{\sum_{i=1}^n\rho_i C_{v,i}\gamma_i}{\sum_{i=1}^n\rho_i C_{v,i}}
$$

は全体の比熱比、$\gamma_i$は成分$i$の比熱比、

$$
C_{v,i}=\frac{R}{\gamma_i-1}
$$

は成分$i$の定積比熱容量です。

成分が1つ以上ある場合、比熱比`gammas`と気体定数`gas_constants`はタプルとして渡す必要があります。例えば、`gammas=(1.4, 1.667)`のように。

残りの変数、例えば定積比熱`cv`や定圧比熱`cp`は、熱的に完璧な気体を考慮して計算されます。
