```
 pclqr(psys, Q, R, S; intpol = true, kwargs...) -> (F, EVALS)
```

最適な周期的安定化ゲイン行列 `F(t)` を計算します。これは、次の形式の連続時間周期状態空間モデル `psys` に対して

```
  .
  x(t) = A(t)x(t) + B(t)u(t) + Bw(t)w(t)
  y(t) = C(t)x(t) + D(t)u(t) + Dw(t)w(t),
```

状態フィードバック制御則

```
 u(t) = F(t)x(t)
```

が二次インデックス

```
 J = Integral {x'(t)Q(t)x(t) + u(t)'R(t)u(t) + 2*x'(t)S(t)u(t)} dt.
```

を最小化するようにします。

次数 `n` のシステムで `m` 入力を持つ場合、`Q(t)` と `R(t)` はそれぞれ `n×n` および `m×m` の対称行列であり、`S(t)` は `n×m` の行列です。行列 `S` は省略された場合はゼロに設定されます。`u(t)` の次元は `R(t)` の次元から推測されます。`R`、`Q` および `S` は定数実行列として代わりに提供することもできます。

また、`A(t)+B(t)F(t)` の閉ループ特性指数 `EVALS` も返されます。

`intpol = true`（デフォルト）の場合、得られた周期的ゲイン `F(t)` は、補間に基づく式を使用して連続時間周期行列微分リカッチ方程式の安定化解から計算されます。`intpol = false` の場合、ゲイン `F(t)` はリカッチ微分方程式の多点解から、対応する常微分方程式の積分を使用して初期条件として最も近い点の値を用いて計算されます。このオプションは、デフォルトで使用されるシンプレクティック積分器と共同で使用することは推奨されません。

`kwargs` に含まれるキーワード引数は、関数 [`PeriodicMatrixEquations.prcric`](@extref) に使用されるものです（`intpol` を除く）。

注意: ペア `(A(t),B(t))` は安定化可能でなければならず、`R` は正定値であり、`[Q S;S' R]` は非負定値でなければなりません。
