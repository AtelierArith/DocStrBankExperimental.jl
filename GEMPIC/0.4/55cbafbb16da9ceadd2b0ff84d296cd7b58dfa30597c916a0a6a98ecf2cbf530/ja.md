```
SumCosGaussian( dims, n_cos, n_gaussians, k, α, σ, μ, δ )
```

初期分布のパラメータのデータ型

$$
(1+ \sum_{i=1}^{n_{cos}} \alpha_i \cos(  k_i \mathbf{x}))
\cdot
\sum_{j=1}^{n_{gaussians}} 
\delta_j \exp 
\big( -\frac{1}{2} 
\frac{(\mathbf{v}-\mu_j)^2}{\sigma_j^2} \big)
$$

## パラメータ

  * `k` : 波数の値（複数のコサイン用のベクトルの配列）
  * `α` : 摂動の強さ
  * `σ` : ガウスの分散（複数のガウス用のベクトルの配列）
  * `μ` : ガウスの平均値（複数のガウス用の配列）
  * `normal` : 各ガウスの正規化定数
  * `n_gaussians` : ガウスの数
  * `n_cos` : コサインの数
  * `δ` : 各ガウスの割合

# 例

$$
f(x,v_1,v_2) = \frac{1}{2\pi\sigma_1\sigma_2} 
\exp \Big( - \frac{1}{2} \big( \frac{v_1^2}{\sigma_1^2}
 + \frac{v_2^2}{\sigma_2^2} \big) \Big) 
( 1 + \alpha_1 \cos(k_1 x) + \alpha_2 \cos(k_2 x) ),
$$

```julia
df = SumCosGaussian{1,2}([[k₁],[k₂]], [α₁, α₂], [[σ₁,σ₂]], [[0.0,0.0]])

```
