```
check_Hessian(M, f, grad_f, Hess_f, p=rand(M), X=rand(M; vector_at=p), Y=rand(M, vector_at=p); kwargs...)
```

Hessian `Hess_f(M,p, X)` が `f(M,p)` の正しさを数値的に検証します。

これには、二次リトラクションまたは `f` の臨界点 $p$ が必要です。近似は次のようになります。

$$
f(\operatorname{retr}_p(tX)) = f(p) + t⟨\operatorname{grad} f(p), X⟩ + \frac{t^2}{2}⟨\operatorname{Hess}f(p)[X], X⟩ + \mathcal O(t^3)
$$

言い換えれば、関数 $f$ とその二次テイラーの間の誤差が $\mathcal O(t^3)$ の誤差で振る舞うことを示しており、これはHessianが正しいことを示しています。詳細は [Boumal:2023; Section 6.8](@cite) を参照してください。

誤差が指定された許容範囲を下回り、メソッドが正確な場合、プロットは生成されません。

# キーワード引数

  * `check_grad=true`: $\operatorname{grad}f(p) ∈ T_{p}\mathcal M$ を検証します。
  * `check_linearity=true`: Hessian が線形であることを検証します。`a`、`b`、`X`、`Y` を使用して [`is_Hessian_linear`](@ref) を参照してください。
  * `check_symmetry=true`: Hessian が対称であることを検証します。[`is_Hessian_symmetric`](@ref) を参照してください。
  * `check_vector=false`: `\operatorname{Hess} f(p)[X] ∈ T_{p}\mathcal M` を検証します。`is_vector` を使用します。
  * `mode=:Default`: 検証のモードを指定します。デフォルトの仮定は、提供されたリトラクションが二次であることです。そうでない場合、点 `p` が臨界点であればHessianを検証することもできます。その場合、モードを `:CritalPoint` に設定して [`gradient_descent`](@ref) を使用して臨界点を見つけます。注意: これには新しい接線ベクトル `X` と `Y` が必要です（評価されます）。
  * `atol`, `rtol`: (デフォルトは `isapprox` と同じ) すべてのチェックに渡される許容範囲。
  * `a`, `b`: Hessian の線形性を検証するための二つの実数値（`check_linearity=true` の場合）。
  * `N=101`: `log_range` のデフォルト範囲 $[10^{-8},10^{0}]$ 内で検証するポイントの数。
  * `exactness_tol=1e-12`: すべての誤差がこの許容範囲を下回る場合、検証は正確と見なされます。
  * `io=nothing`: 結果を出力するための `IO` を提供します。
  * `gradient=grad_f(M, p)`: 勾配関数の代わりに、`p` での勾配を直接提供できます。
  * `Hessian=Hess_f(M, p, X)`: Hessian 関数の代わりに、$\operatorname{Hess} f(p)[X]$ の結果を直接提供できます。線形性と対称性をチェックするためにHessianの評価が必要な場合があります。また、`:CriticalPoint` モードを使用する場合にも必要です。
  * `limits=(-8.0, 0.0)`: `log_range` の限界を指定します。
  * `log_range=range(limits[1], limits[2]; length=N)`: Hessian の線をサンプリングするポイントの範囲（対数スケール）を指定します。
  * `N=101`: `log_range` のデフォルト範囲 $[10^{-8},10^{0}]$ 内で使用するポイントの数。
  * `plot=false`: 結果の検証をプロットするかどうか（`Plots.jl` がロードされている必要があります）。プロットは対数-対数スケールです。これは返され、保存することもできます。
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用するリトラクション $\operatorname{retr}$ を指定します。リトラクションに関するセクションを参照してください [the section on retractions](@extref ManifoldsBase :doc:`retractions`)。
  * `slope_tol=0.1`: 近似の傾き（グローバル）に対する許容範囲。
  * `error=:none`: エラーの処理方法。可能な値: `:error`, `:info`, `:warn`。
  * `window=nothing`: 傾き推定に使用される `log_range` 内のウィンドウサイズを指定します。デフォルトは、すべてのウィンドウサイズ `2:N` を使用します。

`kwargs...` は `check_vector` および `check_gradient` 呼び出しにも渡されるため、許容範囲を簡単に設定できます。

`check_vector` は `check_gradient` への内部呼び出しにも渡されますが、この内部の `check_gradient` は内部検証のためのものであり、エラーをスローしたりプロットを生成したりすることはありません。 ```
