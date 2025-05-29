```
CompressibleNavierStokesDiffusion1D(equations; mu, Pr,
                                    gradient_variables=GradientVariablesPrimitive())
```

質量、運動量、全エネルギーに適用される拡散（すなわち、放物）項と、[`CompressibleEulerEquations1D`](@ref)からの対流項を含みます。

  * `equations`: [`CompressibleEulerEquations1D`](@ref)のインスタンス
  * `mu`: 動的粘度、
  * `Pr`: プラントル数、
  * `gradient_variables`: 勾配がどの変数に対して取られるか。デフォルトは`GradientVariablesPrimitive()`です。

動的粘度 $\mu$ などの流体特性は、任意の一貫した単位系で提供できます。例えば、[$\mu$] = kg m⁻¹ s⁻¹。粘度 $\mu$ は定数であるか、現在の状態の関数である可能性があります。例えば、温度に依存する場合（サザーランドの法則）：$\mu = \mu(T)$。後者の場合、関数 `mu` は `mu(u, equations)` のシグネチャを持つ必要があります。

実装されている可圧ナビエ-ストークスの特定の形式は次の通りです。

$$
\frac{\partial}{\partial t}
\begin{pmatrix}
\rho \\ \rho v \\ \rho e
\end{pmatrix}
+
\frac{\partial}{\partial x}
\begin{pmatrix}
 \rho v \\ \rho v^2 + p \\ (\rho e + p) v
\end{pmatrix}
=
\frac{\partial}{\partial x}
\begin{pmatrix}
0 \\ \tau \\ \tau v - q
\end{pmatrix}
$$

ここで、システムは理想気体の仮定で閉じられ、次のように圧力が与えられます。

$$
p = (\gamma - 1) \left( \rho e - \frac{1}{2} \rho v^2 \right)
$$

断熱定数 `gamma` の値は、[`CompressibleEulerEquations1D`](@ref)から取られます。上記のシステムの右辺の項は、粘性応力から構築されます。

$$
\tau = \mu \frac{\partial}{\partial x} v
$$

熱流束は次のようになります。

$$
q = -\kappa \frac{\partial}{\partial x} \left(T\right),\quad T = \frac{p}{R\rho}
$$

ここで、$T$ は温度、$\kappa$ はフィックの法則における熱伝導率です。気体が一定のプラントル数を持つという仮定の下で、熱伝導率は次のようになります。

$$
\kappa = \frac{\gamma \mu R}{(\gamma - 1)\textrm{Pr}}.
$$

この温度 $T$ と熱伝導率 $\kappa$ の組み合わせから、気体定数 `R` がキャンセルされ、熱流束は次のようになります。

$$
q = -\kappa \frac{\partial}{\partial x} \left(T\right) = -\frac{\gamma \mu}{(\gamma - 1)\textrm{Pr}} \frac{\partial}{\partial x} \left(\frac{p}{\rho}\right)
$$

これは、[`flux`](@ref) 関数で実装されている形式です。

1次元空間では、2つの量の勾配が必要です。例えば、原始量

$$
\frac{\partial}{\partial x} v,\, \frac{\partial}{\partial x} T
$$

またはエントロピー変数

$$
\frac{\partial}{\partial x} w_2,\, \frac{\partial}{\partial x} w_3
$$

ここで、

$$
w_2 = \frac{\rho v1}{p},\, w_3 = -\frac{\rho}{p}
$$
