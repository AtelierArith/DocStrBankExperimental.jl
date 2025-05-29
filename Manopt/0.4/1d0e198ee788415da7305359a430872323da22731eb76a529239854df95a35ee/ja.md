```
check_Hessian(M, f, grad_f, Hess_f, p=rand(M), X=rand(M; vector_at=p), Y=rand(M, vector_at=p); kwargs...)
```

Hessian $\operatorname{Hess} f(M,p, X)$ が `f(M,p)` の正しさを数値的に検証します。

これには、二次のリトラクションまたは `f` の臨界点 $p$ が必要です。近似は次のようになります。

$$
f(\operatorname{retr}_p(tX)) = f(p) + t⟨\operatorname{grad} f(p), X⟩ + \frac{t^2}{2}⟨\operatorname{Hess}f(p)[X], X⟩ + \mathcal O(t^3)
$$

言い換えれば、関数 $f$ とその二次テイラーの間の誤差が $\mathcal O(t^3)$ の誤差で振る舞うことを示しており、これはヘッセ行列が正しいことを示しています。詳細は [Boumal:2023; Section 6.8](@cite) を参照してください。

誤差が指定された許容範囲を下回り、メソッドが正確である場合、プロットは生成されません。

# キーワード引数

  * `check_grad`:       (`true`) $\operatorname{grad} f(p) ∈ T_p\mathcal M$ を検証します。
  * `check_linearity`:  (`true`) ヘッセ行列が線形であることを検証します。`a`、`b`、`X`、および `Y` を使用して [`is_Hessian_linear`](@ref) を参照してください。
  * `check_symmetry`:   (`true`) ヘッセ行列が対称であることを検証します。[`is_Hessian_symmetric`](@ref) を参照してください。
  * `check_vector`:     (`false`) $\operatorname{Hess} f(p)[X] ∈ T_p\mathcal M$ を `is_vector` を使用して検証します。
  * `mode`:             (`:Default`) 検証のモードを指定します。デフォルトの仮定は、提供されたリトラクションが二次であることです。そうでない場合、点 `p` が臨界点である場合にもヘッセ行列を検証できます。その場合、モードを `:CriticalPoint` に設定して [`gradient_descent`](@ref) を使用して臨界点を見つけます。注意: これには新しい接線ベクトル `X` と `Y` が必要です（評価されます）。
  * `atol`, `rtol`:      (デフォルトは `isapprox` と同じ) すべてのチェックに渡される許容範囲。
  * `a`, `b`            ヘッセ行列の線形性を検証するための2つの実数値（`check_linearity=true` の場合）。
  * `N`:                 (`101`) `log_range` のデフォルト範囲 $[10^{-8},10^{0}]$ 内で検証するポイントの数。
  * `exactness_tol`:     (`1e-12`) すべての誤差がこの許容範囲を下回る場合、検証は正確と見なされます。
  * `io`:                (`nothing`) 結果を出力するための `IO` を提供します。
  * `gradient`:          (`grad_f(M, p)`) 勾配関数の代わりに、`p` での勾配を直接提供できます。
  * `Hessian`:           (`Hess_f(M, p, X)`) ヘッセ行列関数の代わりに、$\operatorname{Hess} f(p)[X]$ の結果を直接提供できます。ヘッセ行列の評価は、線形性と対称性のチェック、または `:CriticalPoint` モードを使用する際に必要な場合があります。
  * `limits`:            (`(1e-8,1)`) `log_range` 内の制限を指定します。
  * `log_range`:         (`range(limits[1], limits[2]; length=N)`) ヘッセ行列の線をサンプリングするためのポイントの範囲（対数スケール）を指定します。
  * `N`:                 (`101`) `log_range` のデフォルト範囲 $[10^{-8},10^{0}]$ 内で使用するポイントの数。
  * `plot`:              (`false`) 結果の検証をプロットするかどうか（`Plots.jl` をロードする必要があります）。プロットは対数-対数スケールです。これが返され、保存することもできます。
  * `retraction_method`: (`default_retraction_method(M, typeof(p))`) 使用するリトラクションメソッド。
  * `slope_tol`:         (`0.1`) 近似の傾き（全体）の許容範囲。
  * `error`:             (`:none`) エラーの処理方法。可能な値: `:error`, `:info`, `:warn`。
  * `window`:            (`nothing`) 傾き推定に使用される `log_range` 内のウィンドウサイズを指定します。デフォルトは、すべてのウィンドウサイズ `2:N` を使用します。

`kwargs...` は `check_vector` および `check_gradient` の呼び出しにも渡されるため、許容範囲を簡単に設定できます。

`check_vector` は `check_gradient` への内部呼び出しにも渡されますが、この内部の `check_gradient` は内部検証のためだけに意図されているため、エラーをスローしたり、プロットを生成したりすることはありません。 ```
