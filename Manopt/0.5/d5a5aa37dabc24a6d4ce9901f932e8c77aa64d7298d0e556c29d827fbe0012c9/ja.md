```
InteriorPointCentralityCondition{CO,R}
```

中心性条件をチェックするファンクタ。

[`interior_point_Newton`](@ref) 内で行われるラインサーチのステップを取得するために、[LaiYoshise:2024](@cite) の第6章では、[El-BakryTapiaTsuchiyaZhang:1996](@cite) の第6章で説明されているユークリッドの場合に触発された以下の追加条件を満たすことを提案しています。

与えられた [`ConstrainedManifoldObjective`](@ref) に対して、[`KKTVectorField`](@ref) $F$ を考慮し、点 $q = (p, λ, μ, s)$ が $\mathcal M × ℝ^m × ℝ^n × ℝ^m$ 上にあり、探索方向 $V = (X, Y, Z, W)$ があるとします。

次に、

$$
τ_1 = \frac{m⋅\min\{ μ ⊙ s\}}{μ^{\mathrm{T}}s}
\quad\text{ および }\quad
τ_2 = \frac{μ^{\mathrm{T}}s}{\lVert F(q) \rVert}
$$

ここで、$⊙$ はハダマール（または要素ごとの）積を示します。

新しい候補 $q(α) = \bigl(p(α), λ(α), μ(α), s(α)\bigr) := (\operatorname{retr}_p(αX), λ+αY, μ+αZ, s+αW)$ に対して、次の2つの関数を定義します。

$$
c_1(α) = \min\{ μ(α) ⊙ s(α) \} - \frac{γτ_1 μ(α)^{\mathrm{T}}s(α)}{m}
\quad\text{ および }\quad
c_2(α) = μ(α)^{\mathrm{T}}s(α) – γτ_2 \lVert F(q(α)) \rVert.
$$

論文では、（アルミホ）ラインサーチが点 $\tilde α$ から始まると述べていますが、$c_1(α) ≥ 0$ および $c_2(α) ≥ 0$ という条件をラインサーチに含める方が簡単です。

ここで定義されたファンクタ `InteriorPointCentralityCondition(cmo, γ, μ, s, normKKT)(N,qα)` はこの条件を評価し、$c_1$ と $c_2$ の両方が非負であれば true を返します。

# フィールド

  * `cmo`: [`ConstrainedManifoldObjective`](@ref)
  * `γ`: 定数
  * `τ1`, `τ2`: 式で与えられた定数。

# コンストラクタ

```
InteriorPointCentralityCondition(cmo, γ)
InteriorPointCentralityCondition(cmo, γ, τ1, τ2)
```

中心性条件を初期化します。パラメータ `τ1`, `τ2` は提供されない場合はゼロに初期化されます。

!!! note
    すべての3つの定数に対しては [`get_parameter`](@ref) を、$γ$ を更新するためには [`set_parameter!`](@ref) を使用し、$τ_1$ と $τ_2$ を更新するには `set_parameter(ipcc, :τ, N, q)` を呼び出して、上記の式に従って両方の $τ_1$ と $τ_2$ を更新します。

