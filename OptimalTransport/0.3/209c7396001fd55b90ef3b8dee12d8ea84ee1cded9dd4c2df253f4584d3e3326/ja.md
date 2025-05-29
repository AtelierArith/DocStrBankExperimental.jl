```
sinkhorn_unbalanced(
    μ, ν, C, proxdivF1!, proxdivF2!, ε;
    atol=0, rtol=atol > 0 ? 0 : √eps, check_convergence=10, maxiter=1_000,
)
```

ソースとターゲットの周辺分布 `μ` と `ν`、サイズ `(length(μ), length(ν))` のコスト行列 `C`、エントロピー正則化パラメータ `ε`、および "proxdiv" 関数 `proxdivF!` と `proxdivG!` を持つソフト周辺制約 $F_1$ と $F_2$ を用いて、バランスの取れていないエントロピー正則化最適輸送問題の最適輸送計画を計算します。

最適輸送計画 `γ` は `C` と同じサイズであり、次の問題を解きます。

$$
\inf_{\gamma} \langle \gamma, C \rangle
+ \varepsilon \Omega(\gamma)
+ F_1(\gamma 1, \mu)
+ F_2(\gamma^{\mathsf{T}} 1, \nu),
$$

ここで、$\Omega(\gamma) = \sum_{i,j} \gamma_{i,j} \log \gamma_{i,j}$ はエントロピー正則化項であり、$F_1(\cdot, \mu)$ と $F_2(\cdot, \nu)$ はソースとターゲットの周辺分布に対するソフト周辺制約です。

関数 `proxdivF1!(s, p, ε)` と `proxdivF2!(s, p, ε)` は、エントロピー正則化パラメータ $\varepsilon$ に対して、$F_1(\cdot, p)$ と $F_2(\cdot, p)$ の "proxdiv" 関数を $s$ で評価します。これらはミューテートし、計算結果で最初の引数 `s` を上書きする必要があります。

数学的には、"proxdiv" 関数は次のように定義されます。

$$
\operatorname{proxdiv}_{F_i}(s, p, \varepsilon)
= \operatorname{prox}^{\operatorname{KL}}_{F_i(\cdot, p)/\varepsilon}(s) \oslash s
$$

ここで、$\oslash$ は要素ごとの除算を示し、$\operatorname{prox}_{F_i(\cdot, p)/\varepsilon}^{\operatorname{KL}}$ は Kullback-Leibler ($\operatorname{KL}$) ダイバージェンスに対する $F_i(\cdot, p)/\varepsilon$ の近接演算子です。これは次のように定義されます。

$$
\operatorname{prox}_{F}^{\operatorname{KL}}(x)
= \operatorname{argmin}_{y} F(y) + \operatorname{KL}(y|x)
$$

特定の $F$ の選択に対して閉じた形で計算できます。たとえば、$F(\cdot, p) = \lambda \operatorname{KL}(\cdot | p)$ ($\lambda > 0$) の場合、

$$
\operatorname{prox}_{F(\cdot, p)/\varepsilon}^{\operatorname{KL}}(x)
= x^{\frac{\varepsilon}{\varepsilon + \lambda}} p^{\frac{\lambda}{\varepsilon + \lambda}},
$$

すべての演算子は点ごとに作用します。[^CPSV18]

`check_convergence` の各ステップで、現在のイテレーションと前のイテレーションのスケーリングファクターのイテレートが `isapprox(vcat(a, b), vcat(aprev, bprev); atol=atol, rtol=rtol)` を満たすかどうかを確認することで、アルゴリズムが収束しているかどうかが評価されます。ここで、`a` と `b` は現在のイテレートで、`aprev` と `bprev` は前のものです。デフォルトの `rtol` は `μ`、`ν`、および `C` のタイプに依存します。`maxiter` 回のイテレーションの後、計算は停止します。

[^CPSV18]: Chizat, L., Peyré, G., Schmitzer, B., & Vialard, F.-X. (2018). [Scaling algorithms for unbalanced optimal transport problems](https://doi.org/10.1090/mcom/3303). Mathematics of Computation, 87(314), 2563–2609.

参照: [`sinkhorn_unbalanced2`](@ref) ```
