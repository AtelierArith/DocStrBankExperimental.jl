```
struct ScaledMonomialBasis{MT<:MP.AbstractMonomial, MV<:AbstractVector{MT}} <: AbstractPolynomialBasis
    monomials::MV
end
```

*スケールモニモニアル基底*（[セクション 3.1.5, BPT12]を参照）で、ベクトル `monomials` のモニモニアルを持ちます。モニモニアル $x^\alpha = x_1^{\alpha_1} \cdots x_n^{\alpha_n}$ の次数 $d = \sum_{i=1}^n \alpha_i$ に対して、基底の対応する多項式は

$$
{d \choose \alpha}^{\frac{1}{2}} x^{\alpha} \quad \text{ ただし } \quad
{d \choose \alpha} = \frac{d!}{\alpha_1! \alpha_2! \cdots \alpha_n!}.
$$

例えば、基底 $[xy^2, xy]$ を使って多項式を作成すると、$\sqrt{3} a xy^2 + \sqrt{2} b xy$ という多項式が生成されます。ここで `a` と `b` は新しい JuMP 決定変数です。多項式 $axy^2 + bxy$ をスケールモニモニアル基底でゼロに制約すると、`a/√3` と `b/√2` がゼロに制約されます。

この基底はスカラー積の下で直交正規です：

$$
\langle f, g \rangle = \int_{\mathcal{C}^n} f(z) \overline{g(z)} d\nu_n
$$

ここで $\nu_n$ は、密度 $\pi^{-n} \exp(-\lVert z \rVert^2)$ を持つ $\mathcal{C}^n$ 上のガウス測度です。詳細については [セクション 4; B07] を参照してください。

[BPT12] Blekherman, G.; Parrilo, P. A. & Thomas, R. R. *半正定値最適化と凸代数幾何学*. Society for Industrial and Applied Mathematics (2012).

[B07] Barvinok, Alexander. *ランダム部分空間への制限による多変数多項式の統合と最適化.* Foundations of Computational Mathematics 7.2 (2007): 229-244.
