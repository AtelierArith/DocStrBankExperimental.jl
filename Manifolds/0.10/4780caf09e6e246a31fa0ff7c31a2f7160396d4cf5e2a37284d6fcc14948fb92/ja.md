```
pX = rand(M::HamiltonianMatrices; σ::Real=1.0, vector_at=nothing)
rand!(M::HamiltonianMatrices, pX; σ::Real=1.0, vector_at=nothing)
```

ランダムなハミルトニアン行列を生成します。これらは $ℝ^{2n×2n}$ の部分多様体であるため、同じ方法が点と接ベクトルに適用されます。これは `pX` のインプレースでも行うことができます。

この構成は、1つの正規分布に従う $n×n$ 行列 $A$ と2つの対称 $n×n$ 行列 $B, C$ を生成し、それらをスタックすることに基づいています：

$$
p = \begin{pmatrix} A & B\\ C & -A^{\mathrm{T}} \end{pmatrix}
$$
