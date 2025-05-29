```
exp(G, X)
exp!(G, g, X)
```

[`OrthogonalGroup`](@ref) $\mathrm{O}(3)$ または [`SpecialOrthogonalGroup`](@ref) $\mathrm{SO}(3)$ 上でのリー群指数関数を計算します。ここで `e` は [`Identity`](@ref)`{MatrixMultiplicationGroupOperation}` であり、`G` はディスパッチのために [`TypeParameter`](@extref `ManifoldsBase.TypeParameter`) を使用します。

両方の群のリー代数は一致し、斜対称行列の集合から成るため、$3×3$ の斜対称行列は次の形をしています。

$$
    X = \begin{pmatrix} 0 & -c & b\\ c & 0 & -a\\ -b & a & 0\end{pmatrix},
$$

ここで $a, b, c ∈ ℝ$ です。指数を計算するために、[ロドリゲスの回転公式](https://en.wikipedia.org/wiki/Olinde_Rodrigues) を使用できます。$α = \sqrt{a^2+b^2+c^2} = \frac{1}{\sqrt{2}}\lVert X \rVert_{}$ とすると、$α ≠ 0$ の場合に次のようになります。

$$
\exp_{\mathcal G}(X) = I_3 + \frac{\sin}{α}X + \frac{(1 - \cos)}{α^2}X^2,
$$

そして \exp*{\mathcal G}(X) = I*3`` それ以外の場合。

この結果は `g` のインプレースで計算できます。

$$
\mathrm{SO}(3)
$$

は二つの互いに素な連結成分から成り、指数写像は滑らかであるため、結果 $g$ は常に単位元の連結成分に存在することに注意してください。
