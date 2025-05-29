```
SpecialEuclidean(n)
```

特別ユークリッド群 $\mathrm{SE}(n)$、剛体運動の群。

$$
\mathrm{SE}(n)
$$

は、$ℝ^n$ 上の [`TranslationGroup`](@ref) と [`SpecialOrthogonal`](@ref)`(n)` の半直積です。

$$
\mathrm{SE}(n) ≐ \mathrm{T}(n) ⋊_θ \mathrm{SO}(n),
$$

ここで、$θ$ はベクトル回転による $\mathrm{SO}(n)$ の $\mathrm{T}(n)$ への標準的な作用です。

このコンストラクタは、次の呼び出しと同等です。

```julia
Tn = TranslationGroup(n)
SOn = SpecialOrthogonal(n)
SemidirectProductGroup(Tn, SOn, RotationAction(Tn, SOn))
```

$$
\mathrm{SE}(n)
$$

上の点は、基礎となる積多様体 $\mathrm{T}(n) × \mathrm{SO}(n)$ 上の点として表現できます。群特有の関数については、サイズ `(n + 1, n + 1)` のアフィン行列としても表現でき（[`affine_matrix`](@ref) を参照）、その場合の群演算は [`MultiplicationOperation`](@ref) です。
