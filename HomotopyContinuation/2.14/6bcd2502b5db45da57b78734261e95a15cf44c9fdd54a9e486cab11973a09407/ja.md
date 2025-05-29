```
certify(F, solutions, [p, certify_cache]; options...)
certify(F, result, [p, certify_cache]; options...)
```

与えられた近似解 `solutions` が多項式系 $F(x;p)$ の真の解に対応することを証明しようとします。系 $F$ は（アフィン）正方形多項式系でなければなりません。また、各解が実際の解に近似しているかどうかを証明しようとします。証明は区間算術とクレイツキ法[^Moo77]を使用して行われます。[`CertificationResult`](@ref) を返し、追加で異なる解の数を返します。実装の詳細については [^BRT20] を参照してください。

## オプション

  * `show_progress = true`: `true` の場合、証明プロセスの進行状況バーを表示します。
  * `max_precision = 256`: 証明プロセスで使用される最大精度（ビット単位）。
  * `compile = false`: [`solve`](@ref) ドキュメントを参照してください。

## 例

私たちは、導入ガイドからの[最初の例](https://www.juliahomotopycontinuation.org/guides/introduction/#a-first-example)を取ります。

```julia
@var x y
# 多項式を定義する
f₁ = (x^4 + y^4 - 1) * (x^2 + y^2 - 2) + x^5 * y
f₂ = x^2+2x*y^2 - 2y^2 - 1/2
F = System([f₁, f₂], variables = [x,y])
result = solve(F)
```

```
18 の解を持つ結果
========================
• 18 の経路が追跡されました
• 18 の非特異解（4 の実解）
• ランダムシード: 0xcaa483cd
• start_system: :polyhedral
```

私たちは18の解を得ており、4つの解が実際であるようです。しかし、これはヒューリスティックに基づいています。絶対的に確実であるために、結果を証明することができます。

```julia
certify(F, result)
```

```
CertificationResult
===================
• 18 の解候補が与えられました
• 18 の証明された解区間（4 の実解、14 の複素解）
• 18 の異なる証明された解区間（4 の実解、14 の複素解）
```

実際に18の解があり、それらがすべて異なることがわかります。

[^Moo77]: Moore, Ramon E. "A test for existence of solutions to nonlinear systems." SIAM Journal on Numerical Analysis 14.4 (1977): 611-615.

[^BRT20]: Breiding, P., Rose, K. and Timme, S. "Certifying zeros of polynomial systems using interval arithmetic." arXiv:2011.05000.
