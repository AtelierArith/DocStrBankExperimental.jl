```
tvcplyap_eval(t, U, A, C; adj = false, solver, reltol, abstol) -> Uval
```

上三角周期生成器 `U(t)` の時間値 `Uval := U(t)` を計算します。これは周期リャプノフ微分方程式の解 `X(t) = U(t)U(t)'` のものです。

```
  .
  X(t) = A(t)X(t) + X(t)A(t)' + C(t)C(t)' , X(t0) = U(t0)U(t0)', t > t0, if adj = false,
```

または、周期リャプノフ微分方程式の解 `X(t) = U(t)'U(t)` のものです。

```
  .
 -X(t) = A(t)'X(t) + X(t)A(t) + C(t)'C(t) , X(t0) = U(t0)'U(t0), t < t0, if adj = true,
```

同じ周期行列 `A` と `C`、およびキーワード引数 `adj` の同じ値で、関数 [`pgcplyap`](@ref) によって決定された周期生成器 `U` を使用します。初期時間 `t0` は、`adj = false` の場合は `t` より下の最も近い時間グリッド値、`adj = true` の場合は上の最も近い時間グリッド値です。

上記の常微分方程式は、キーワード引数 `solver` で指定された積分法を用いて解かれます。必要な相対精度 `reltol`（デフォルト: `reltol = 1.e-4`）、絶対精度 `abstol`（デフォルト: `abstol = 1.e-7`）、およびステップサイズ `dt`（デフォルト: `dt = 0`、`solver = "symplectic"` の場合のみ使用）とともに使用されます。希望する相対精度 `reltol` に応じて、`reltol >= 1.e-4` の場合は低次のソルバーが使用され、一般的に非常に効率的ですが、精度は低くなります。`reltol < 1.e-4` の場合は、高精度の要求に対応できる高次のソルバーが使用されます。

以下のソルバーは、[OrdinaryDiffEq.jl](https://github.com/SciML/OrdinaryDiffEq.jl) パッケージから選択できます：

`solver = "non-stiff"` - 非剛性問題用のソルバーを使用します（`Tsit5()` または `Vern9()`）;

`solver = "stiff"` - 剛性問題用のソルバーを使用します（`Rodas4()` または `KenCarp58()`）;

`solver = "auto"` - デフォルトのソルバーを使用し、剛性問題を自動的に検出します（`AutoTsit5(Rosenbrock23())` または `AutoVern9(Rodas5()`）。
