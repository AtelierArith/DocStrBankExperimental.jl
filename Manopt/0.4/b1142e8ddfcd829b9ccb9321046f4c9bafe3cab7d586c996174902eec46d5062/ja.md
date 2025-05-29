```
ExactPenaltyCost{S, Pr, R}
```

正確ペナルティ法のコストを、[`ConstrainedManifoldObjective`](@ref) `P` とパラメータ $ρ$ に基づいて表します。

$$
f(p) + ρ\Bigl(
    \sum_{i=0}^m \max\{0,g_i(p)\} + \sum_{j=0}^n \lvert h_j(p)\rvert
\Bigr),
$$

ここで、追加のパラメータ $u$ が使用され、スムージング技術（例えば、[`LogarithmicSumOfExponentials`](@ref) または [`LinearQuadraticHuber`](@ref)）を用いて滑らかなコスト関数を得ます。この構造体は、コスト $v$ のファンクタ `(M,p) -> v` でもあります。

## フィールド

  * `ρ`, `u`: 数式で説明されているように。
  * `co`:     元のコスト

## コンストラクタ

```
ExactPenaltyCost(co::ConstrainedManifoldObjective, ρ, u; smoothing=LinearQuadraticHuber())
```
