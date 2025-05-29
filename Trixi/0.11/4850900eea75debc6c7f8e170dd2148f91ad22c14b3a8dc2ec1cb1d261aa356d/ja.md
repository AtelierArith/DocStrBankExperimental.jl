```
CompressibleEulerEquationsQuasi1D(gamma)
```

準1次元可圧縮オイラー方程式（詳細についてはChan et al. [DOI: 10.48550/arXiv.2307.12089](https://doi.org/10.48550/arXiv.2307.12089) を参照）

$$
\frac{\partial}{\partial t}
\begin{pmatrix}
a \rho \\ a \rho v_1 \\ a e
\end{pmatrix}
+
\frac{\partial}{\partial x}
\begin{pmatrix}
a \rho v_1 \\ a \rho v_1^2 \\ a v_1 (e +p)
\end{pmatrix}
+ 
a \frac{\partial}{\partial x}
\begin{pmatrix}
0 \\ p \\ 0    
\end{pmatrix}
=
\begin{pmatrix}
0 \\ 0 \\ 0
\end{pmatrix}
$$

理想気体の比熱比 `gamma` における1次元空間。ここで、$\rho$ は密度、$v_1$ は速度、$e$ は特定の総エネルギー **ではなく** 特定の内部エネルギー、$a$ は（おそらく）可変のノズル幅、そして

$$
p = (\gamma - 1) \left( e - \frac{1}{2} \rho v_1^2 \right)
$$

は圧力です。

ノズル幅関数 $a(x)$ は特定の問題設定の初期条件ルーチン内で設定されます。可圧縮オイラー方程式の保存形式をテストするために、ノズル幅変数 $a$ を1に設定することができます。

未知数に加えて、Trixi.jl は現在、時間的に固定されているにもかかわらず、近似点でのノズル幅の値を保存します。これは、これらの方程式の実装と使用にさまざまな影響を与えます：

  * ノズル幅に対応するフラックス値はゼロでなければなりません。
  * 初期条件、境界条件、またはソース項を定義する際にノズル幅の値を含める必要があります。
  * [`AnalysisCallback`](@ref) はこの変数を分析します。
  * Trixi.jl の視覚化ツールはデフォルトでノズル幅を視覚化します。
