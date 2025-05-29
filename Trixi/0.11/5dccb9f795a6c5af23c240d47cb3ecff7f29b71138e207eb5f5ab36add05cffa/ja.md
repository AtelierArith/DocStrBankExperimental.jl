```
CompressibleNavierStokesDiffusion2D(equations; mu, Pr,
                                    gradient_variables=GradientVariablesPrimitive())
```

質量、運動量、全エネルギーに適用される拡散（すなわち、放物）項と、[`CompressibleEulerEquations2D`](@ref)からの対流項を含みます。

  * `equations`: [`CompressibleEulerEquations2D`](@ref) のインスタンス
  * `mu`: 動的粘度、
  * `Pr`: プラントル数、
  * `gradient_variables`: 勾配がどの変数に対して取られるか。デフォルトは `GradientVariablesPrimitive()` です。

動的粘度 $\mu$ などの流体特性は、一貫した単位系で提供できます。例えば、[$\mu$] = kg m⁻¹ s⁻¹。粘度 $\mu$ は定数であるか、現在の状態の関数である可能性があります。例えば、温度に依存する場合（サザーランドの法則）：$\mu = \mu(T)$。後者の場合、関数 `mu` は `mu(u, equations)` のシグネチャを持つ必要があります。

実装されている可圧ナビエ-ストークスの特定の形式は次の通りです。

$$
\frac{\partial}{\partial t}
\begin{pmatrix}
\rho \\ \rho \mathbf{v} \\ \rho e
\end{pmatrix}
+
\nabla \cdot
\begin{pmatrix}
 \rho \mathbf{v} \\ \rho \mathbf{v}\mathbf{v}^T + p \underline{I} \\ (\rho e + p) \mathbf{v}
\end{pmatrix}
=
\nabla \cdot
\begin{pmatrix}
0 \\ \underline{\tau} \\ \underline{\tau}\mathbf{v} - \mathbf{q}
\end{pmatrix}
$$

ここで、システムは理想気体の仮定で閉じられ、次のように圧力が与えられます。

$$
p = (\gamma - 1) \left( \rho e - \frac{1}{2} \rho (v_1^2+v_2^2) \right)
$$

断熱定数 `gamma` の値は [`CompressibleEulerEquations2D`](@ref) から取られます。上記のシステムの右辺の項は、粘性応力テンソルから構築されます。

$$
\underline{\tau} = \mu \left(\nabla\mathbf{v} + \left(\nabla\mathbf{v}\right)^T\right) - \frac{2}{3} \mu \left(\nabla\cdot\mathbf{v}\right)\underline{I}
$$

ここで、$\underline{I}$ は $2\times 2$ の単位行列であり、熱流束は次のようになります。

$$
\mathbf{q} = -\kappa\nabla\left(T\right),\quad T = \frac{p}{R\rho}
$$

ここで、$T$ は温度、$\kappa$ はフィックの法則における熱伝導率です。気体が一定のプラントル数を持つという仮定の下で、熱伝導率は次のようになります。

$$
\kappa = \frac{\gamma \mu R}{(\gamma - 1)\textrm{Pr}}.
$$

この温度 $T$ と熱伝導率 $\kappa$ の組み合わせから、気体定数 `R` がキャンセルされ、熱流束は次のようになります。

$$
\mathbf{q} = -\kappa\nabla\left(T\right) = -\frac{\gamma \mu}{(\gamma - 1)\textrm{Pr}}\nabla\left(\frac{p}{\rho}\right)
$$

これは、[`flux`](@ref) 関数で実装されている形式です。

2次元空間では、3つの量の勾配が必要です。例えば、原始量

$$
\nabla v_1,\, \nabla v_2,\, \nabla T
$$

またはエントロピー変数

$$
\nabla w_2,\, \nabla w_3,\, \nabla w_4
$$

ここで

$$
w_2 = \frac{\rho v_1}{p},\, w_3 = \frac{\rho v_2}{p},\, w_4 = -\frac{\rho}{p}
$$
