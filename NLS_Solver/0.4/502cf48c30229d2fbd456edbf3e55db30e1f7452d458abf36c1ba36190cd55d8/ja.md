```julia
abstract type AbstractNLS end 
```

非線形最小二乗問題（NLS）の抽象型を定義します。この文脈において、その問題は本質的に微分可能な関数 $\mathbf{r}$ です：

$$
\mathbf{r}: \theta\in\mathbb{R}^{n_θ}\mapsto \mathbf{r}(\mathbf{\theta})\in\mathbb{R}^{n_S}
$$

ここで：

  * $$
    \mathbf{r}(\mathbf{θ})∈\mathbb{R}^{n_S}
    $$

    は残差ベクトル、
  * $$
    \mathbf{θ}∈\mathbb{R}^{n_θ}
    $$

    は最適化されるパラメータベクトルです。

最小化すべき目的関数は次の通りです：

$$
f(θ)=\frac{1}{2}\| \mathbf{r}(θ) \|^2
$$

古典的なアプローチは、$\mathbf{r}$ の線形近似を使用します：

$$
\mathbf{r}(\mathbf{θ}+δ\mathbf{θ})\approx \mathbf{r}(\mathbf{θ}) + \mathbf{J}(\mathbf{θ})\cdot δ\mathbf{θ}
$$

ここで、$\mathbf{J}$ はヤコビアンです：

$$
\mathbf{J}_{i,j}=\partial_j r^i(\mathbf{θ}),\ i\in[1,n_S],\ j\in[1,n_θ]
$$

これにより、

$$
f(\mathbf{θ}+δ\mathbf{θ})\approx f(\mathbf{θ}) + \langle \nabla f, δ\mathbf{θ} \rangle + \frac{1}{2}  \langle \nabla^2 f \cdot δ\mathbf{θ},  δ\mathbf{θ} \rangle
$$

勾配 $\nabla f$ は $\mathbf{J}^t \mathbf{r}$ であり、（近似的な）ヘッセ行列 $\nabla^2 f$ は $\mathbf{J}^t \mathbf{J}$ です。

このようなモデルを実装するには、次の関数を定義する必要があります：

  * [`parameter_size`](@ref) : $n_θ$ を返します
  * [`residue_size`](@ref) : $n_S$ を返します
  * [`eval_r`](@ref) : $\mathbf{r}$ を計算します
  * [`eval_r_J`](@ref) : $(\mathbf{r}, \mathbf{J})$ を計算します
