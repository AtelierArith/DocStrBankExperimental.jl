```
AcousticPerturbationEquations2D(v_mean_global, c_mean_global, rho_mean_global)
```

二次元空間における音響摂動方程式（APE）。方程式は次のように与えられます。

$$
\begin{aligned}
  \frac{\partial\mathbf{v'}}{\partial t} + \nabla (\bar{\mathbf{v}}\cdot\mathbf{v'})
    + \nabla\left( \frac{\bar{c}^2 \tilde{p}'}{\bar{\rho}} \right) &= 0 \\
  \frac{\partial \tilde{p}'}{\partial t} +
    \nabla\cdot (\bar{\rho} \mathbf{v'} + \bar{\mathbf{v}} \tilde{p}') &= 0.
\end{aligned}
$$

バー記号 $\bar{(\cdot)}$ は時間平均された量を示します。APEの未知数は摂動速度 $\mathbf{v'} = (v_1', v_2')^T$ とスケールされた摂動圧力 $\tilde{p}' = \frac{p'}{\bar{c}^2}$ であり、ここで $p'$ は摂動圧力を示し、摂動変数は $\phi' = \phi - \bar{\phi}$ によって定義されます。

未知数に加えて、Trixi.jl は現在、状態ベクトルに平均値を格納しています。すなわち、内部で使用される状態ベクトルは次のように与えられます。

$$
\mathbf{u} =
  \begin{pmatrix}
    v_1' \\ v_2' \\ \tilde{p}' \\ \bar{v}_1 \\ \bar{v}_2 \\ \bar{c} \\ \bar{\rho}
  \end{pmatrix}.
$$

これは、これらの方程式の実装と使用にさまざまな影響を与えます：

  * 平均値に対応するフラックス値はゼロでなければなりません。
  * 初期条件、境界条件、またはソース項を定義する際には平均値を考慮する必要があります。
  * [`AnalysisCallback`](@ref) はこれらの変数も分析します。
  * Trixi.jl の可視化ツールはデフォルトで平均値を可視化します。

コンストラクタは、2-タプル `v_mean_global` とスカラー `c_mean_global` および `rho_mean_global` を受け入れ、定常平均流を持つ問題の初期条件の定義をより柔軟にするために使用できます。これらの値は、初期条件内で平均値が内部的に定義されている場合は無視されます。

方程式は、次の論文で紹介された APE-4 システムに基づいています：

  * Roland Ewert と Wolfgang Schröder (2003) 音響摂動方程式は、ソースフィルタリングによる流れの分解に基づいています [DOI: 10.1016/S0021-9991(03)00168-2](https://doi.org/10.1016/S0021-9991(03)00168-2)
