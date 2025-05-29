```
GradientCorrection()
```

粒子相互作用の修正された勾配を、相対位置に基づいて計算します（[Bonet, 1999](@cite Bonet1999)を参照）。

# 数学的詳細

標準的なSPH表現において、粒子$a$における場$A$の勾配は次のように与えられます。

$$
\nabla A_a = \sum_b m_b \frac{A_b - A_a}{\rho_b} \nabla_{r_a} W(\Vert r_a - r_b \Vert, h),
$$

ここで、$m_b$は粒子$b$の質量、$\rho_b$は粒子$b$の密度です。

一般的に提案される勾配補正は、この勾配に補正行列$L$を掛けることを含みます：

$$
\tilde{\nabla} A_a = \bm{L}_a \nabla A_a
$$

補正行列$\bm{L}_a$は、提供された粒子配置に基づいて計算され、特に領域の境界付近で修正された勾配をより正確にすることを目的としています。

次の条件を満たすために

$$
\sum_b V_b r_{ba} \otimes \tilde{\nabla}W_b(r_a) = \left( \sum_b V_b r_{ba} \otimes \nabla W_b(r_a) \right) \bm{L}_a^T = \bm{I}
$$

補正行列$\bm{L}_a$は明示的に次のように評価されます。

$$
\bm{L}_a = \left( \sum_b V_b \nabla W_b(r_{a}) \otimes r_{ba} \right)^{-1}.
$$

!!! note
      * 粒子が小さなクラスターに分離する際に、安定性の問題が発生します。
      * 計算コストが倍増します。
      * より大きなサポートを持つ滑らかなスムージングカーネル（例：[`SchoenbergQuinticSplineKernel`](@ref)や[`WendlandC6Kernel`](@ref)）を使用することで、より良い安定性が得られます。
      * 安定性のために`dt_max =< 1e-3`を設定してください。

