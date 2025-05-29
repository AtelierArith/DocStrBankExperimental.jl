```
LatticeBoltzmannEquations2D(; Ma, Re, collision_op=collision_bgk,
                           c=1, L=1, rho0=1, u0=nothing, nu=nothing)
```

ラティス・ボルツマン方程式

$$
\partial_t u_\alpha + v_{\alpha,1} \partial_1 u_\alpha + v_{\alpha,2} \partial_2 u_\alpha = 0
$$

二次元空間におけるD2Q9スキームのための。

特性マッハ数とレイノルズ数はそれぞれ`Ma`と`Re`として指定されます。デフォルトでは、衝突オペレーター`collision_op`はBGKモデルに設定されています。`c`、`L`、および`rho0`はそれぞれ平均熱分子速度、特性長さ、および基準密度を指定します。通常、これらはデフォルト値のままにしておくことができます。必要に応じて、マッハ数の代わりに、巨視的基準速度`u0`を直接設定することができます（この場合、`Ma`は`nothing`に設定する必要があります）。同様に、レイノルズ数の代わりに運動粘度`nu`を直接指定することができます（この場合、`Re`は`nothing`に設定する必要があります）。

D2Q9スキームの9つの離散速度方向は次のように並べられています [4]:

```
  6     2     5       y
    ┌───┼───┐         │
    │       │         │
  3 ┼   9   ┼ 1        ──── x
    │       │        ╱
    └───┼───┘       ╱
  7     4     8    z
```

通常、速度は`0`から`8`まで番号が付けられ、`0`はゼロ速度に対応します。Juliaが1ベースのインデックスを使用しているため、ここでは`1`から`9`までのインデックスを使用し、`1`から`8`は[4]の速度方向に対応し、`9`はゼロ速度です。

対応する反対方向は次の通りです：

  * 1 ←→ 3
  * 2 ←→ 4
  * 3 ←→ 1
  * 4 ←→ 2
  * 5 ←→ 7
  * 6 ←→ 8
  * 7 ←→ 5
  * 8 ←→ 6
  * 9 ←→ 9

基本実装の主な情報源は次の通りです。

1. Misun Min, Taehun Lee, **A spectral-element discontinuous Galerkin lattice Boltzmann method for nearly incompressible flows**, Journal of Computational Physics 230(1), 2011 [doi:10.1016/j.jcp.2010.09.024](https://doi.org/10.1016/j.jcp.2010.09.024)
2. Karsten Golly, **Anwendung der Lattice-Boltzmann Discontinuous Galerkin Spectral Element Method (LB-DGSEM) auf laminare und turbulente nahezu inkompressible Strömungen im dreidimensionalen Raum**, Master Thesis, University of Cologne, 2018.
3. Dieter Hänel, **Molekulare Gasdynamik**, Springer-Verlag Berlin Heidelberg, 2004 [doi:10.1007/3-540-35047-0](https://doi.org/10.1007/3-540-35047-0)
4. Timm Krüger et al., **The Lattice Boltzmann Method**, Springer International Publishing, 2017 [doi:10.1007/978-3-319-44649-3](https://doi.org/10.1007/978-3-319-44649-3)
