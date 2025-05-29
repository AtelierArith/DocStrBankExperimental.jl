```
t, ht, nbk, nbG = armijo_goldstein(h, h₀, slope)
```

`d`によって定義された方向に沿って`x`から線形探索を行います。ここで、`LineModel`により`h(t) = f(x + t d)`と定義され、`h₀ = h(0) = f(x)`、`slope = h'(0) = ∇f(x)ᵀd`です。ステップ長はArmijo-Goldstein条件を満たすように選択されます。Armijo条件は次のようになります。

$$
h(t) ≤ h₀ + τ₀ t h'(0)
$$

Goldstein条件は次のようになります。

$$
h(t) ≥ h₀ + τ₁ t h'(0).
$$

ここで、`0 < τ₀ < τ₁ < 1`です。

# 引数

  * `h::LineModel{T, S, M}`: 探索方向`d`に沿った1次元モデル、$h(t) = f(x + t d)$
  * `h₀::T`: `t = 0`における`h`の値
  * `slope`: 勾配と探索方向のドット積、$∇f(x)ᵀd$

# キーワード引数

  * `t::T = one(T)`: 初期ステップ長（デフォルト: `1`）;
  * `τ₀::T = T(eps(T)^(1/4))`: Armijo条件におけるスロープ因子。`0 < τ₀ < τ₁ < 1`を満たす必要があります;
  * `τ₁::T = min(T(1)-eps(T), T(0.9999))`: Goldstein条件におけるスロープ因子。`0 < τ₀ < τ₁ < 1`を満たす必要があります;
  * `γ₀::T = T(1 / 2)`: バックトラッキングステップ長の乗数因子（0 < γ₀ <1）
  * `γ₁::T = T(2)`: 先読みステップ長の乗数因子（γ₁ > 1）
  * `bk_max`: 最大バックトラック数（デフォルト: `10`）;
  * `bG_max`: 最大増加数（デフォルト: `10`）;
  * `verbose`: 情報を印刷するかどうか（デフォルト: `false`）。

# 出力

  * `t::T`: ステップ長;
  * `ht::T`: `t`におけるモデル値、すなわち`f(x + t * d)`;
  * `nbk::Int`: Armijo条件を満たすためにステップ長が減少した回数、すなわちバックトラックの回数;
  * `nbG::Int`: Goldstein条件を満たすためにステップ長が増加した回数。

# 参考文献

この実装は次の記述に従っています。

```
C. Cartis, P. R. Sampaio, Ph. L. Toint,
Worst-case evaluation complexity of non-monotone gradient-related algorithms for unconstrained optimization.
Optimization 64(5), 1349–1361 (2015).
DOI: 10.1080/02331934.2013.869809
```

このメソッドは、Armijo条件とGoldstein条件の両方を満たす点を含むことが保証された区間`[t_low,t_up]`を初期化し、その後バイセクションアルゴリズムを使用してそのような点を見つけます。このメソッドはM=0で実装されており（参照を参照）、すなわちArmijo条件とGoldstein条件は目的関数の現在の値`h₀`に対してのみ満たされます。

# 例

```jldoctest; output = false
using SolverTools, ADNLPModels
nlp = ADNLPModel(x -> x[1]^2 + 4 * x[2]^2, ones(2))
lm = LineModel(nlp, nlp.meta.x0, -ones(2))

t, ft, nbk, nbG = armijo_goldstein(lm, obj(lm, 0.0), grad(lm, 0.0))

# output

(1.0, 0.0, 0, 0)
```
