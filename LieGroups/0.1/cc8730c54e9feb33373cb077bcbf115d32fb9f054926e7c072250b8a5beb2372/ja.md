```
exp(G, X)
exp!(G, g, X)
```

[`OrthogonalGroup`](@ref) $\mathrm{O}(2)$ または [`SpecialOrthogonalGroup`](@ref) $\mathrm{SO}(2)$ 上でのリー群指数関数を計算します。ここで `e` は [`Identity`](@ref)`{MatrixMultiplicationGroupOperation}` であり、`G` はディスパッチのために [`TypeParameter`](@extref `ManifoldsBase.TypeParameter`) を使用します。

両方の群のリー代数は一致し、斜対称行列の集合から成るため、$2×2$ 行列の場合、これらは $X=\begin{pmatrix} 0 & -α\\ α & 0\end{pmatrix}$ に簡略化されます。ここで、$α∈ℝ$ です。

その指数は次のようになります。

$$
\exp_{\mathcal G}(X) =  \begin{pmatrix} \cos(α) & -\sin(α)\\ \sin(α) & \cos(α)\end{pmatrix}.
$$

この結果は `g` のインプレースで計算できます。

$$
\mathrm{O}(2)
$$

は二つの離散的な連結成分から成り、指数写像は滑らかであるため、結果 $g$ は常に単位元の連結成分に存在します。
